# Ex.No: 1B                     CONVERSION OF NON STATIONARY TO STATIONARY DATA

### Developed by: A.Sasi Dharan
### Register Number: 212221240049
# Date: 

### AIM:
To perform regular differncing,seasonal adjustment and log transformatio on Global Temperatuer data
### ALGORITHM:
1. Import the required packages like pandas and numpy
2. Read the data using the pandas
3. Perform the data preprocessing if needed and apply regular differncing,seasonal adjustment,log transformation.
4. Plot the data according to need, before and after regular differncing,seasonal adjustment,log transformation.
5. Display the overall results.
### PROGRAM:
~~~
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
file_path = '/content/climate_data.csv'
data = pd.read_csv(file_path)
data['dt'] = pd.to_datetime(data['dt']) 
data.set_index('dt', inplace=True)  
data.fillna(method='ffill', inplace=True)  
# Changed watertemp to globaltemp
globaltemp_data = data['AverageTemperature']
# Plot Original Data for GlobalTemp (C)
plt.figure(figsize=(14, 8))
plt.plot(globaltemp_data, label='GlobalTemp (C)')
plt.title('Original GlobalTemp (C) Data')
plt.legend()
plt.show()
# Regular Differencing for GlobalTemp (C)
globaltemp_diff = globaltemp_data.diff().dropna()
# Plot Differenced Data for GlobalTemp (C)
plt.figure(figsize=(14, 8))
plt.plot(globaltemp_diff, label='GlobalTemp (C) (Diff)') 
plt.title('Differenced GlobalTemp (C) Data')
plt.legend()
plt.show()
# Log Transformation for GlobalTemp (C)
globaltemp_log = np.log(globaltemp_data + 1)  
# Plot Log-Transformed Data for GlobalTemp (C)
plt.figure(figsize=(14, 8))
plt.plot(globaltemp_log, label='GlobalTemp (C) (Log)') 
plt.title('Log-Transformed GlobalTemp (C) Data') 
plt.legend()
plt.show()
# Seasonal Adjustment (using moving average) for GlobalTemp (C)
globaltemp_seasonal_adjustment = globaltemp_log - globaltemp_log.rolling(window=7).mean()
globaltemp_seasonal_adjustment.dropna(inplace=True)
plt.figure(figsize=(14, 8))
plt.plot(globaltemp_seasonal_adjustment, label='GlobalTemp (C) (Seasonally Adjusted)') 
plt.title('Seasonally Adjusted Log-Transformed GlobalTemp (C) Data')
plt.legend()
plt.show()
~~~

### OUTPUT:

![image](https://github.com/user-attachments/assets/b7b73f96-e624-43f0-be28-6ae7edb6eaec)

REGULAR DIFFERENCING:

![image](https://github.com/user-attachments/assets/52f6097d-8339-4f99-8956-df528c6e89dd)

SEASONAL ADJUSTMENT:
![image](https://github.com/user-attachments/assets/9eb4bd79-9a40-4bf3-be7f-5e72e3912551)


LOG TRANSFORMATION:

![image](https://github.com/user-attachments/assets/aa1bf7f2-dbf7-4ebd-b660-b5ac586d0d18)


### RESULT:
Thus the python code for the conversion of non stationary to stationary data on Global Temperatuer data.
