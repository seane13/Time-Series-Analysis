# Time-Series and Linear Regression for analysis and forecasting. 

This project uses 2 Jupyter notebooks for analysis of the Japanese Yen compared to the US Dollar. The following imports will be needed to run these notebooks.

* import numpy as np
* import pandas as pd
* from pathlib import Path
* import statsmodels.api as sm
* from statsmodels.tsa.arima_model import ARMA
* from statsmodels.tsa.arima_model import ARIMA
* import arch as arch
* from arch import arch_model
* from statsmodels.tsa.stattools import adfuller
* from sklearn.linear_model import LinearRegression
* from sklearn.metrics import mean_squared_error
* %matplotlib inline

### The first notebook focuses on Time-Series Forecasting.

In this notebook, I will load historical Dollar-Yen exchange rate futures data and apply time series analysis and modeling to determine whether there is any predictable behavior. I will be using the following guidelines. 

1. Decomposition using a Hodrick-Prescott Filter (Decompose the Settle price into trend and noise).
2. Forecasting Returns using an ARMA Model.
3. Forecasting the Settle Price using an ARIMA Model.
4. Forecasting Volatility with GARCH.

I will use the results of the time series analysis and modeling to answer the following questions:

1. Based on the time series analysis, should I buy the yen now?
2. Is the risk of the yen expected to increase or decrease?
3. Based on the model evaluation, do I feel confident in using these models for trading?


### The second notebook focuses on Linear Regression Forecasting.

In this notebook, I will build a Scikit-Learn linear regression model to predict Yen futures ("settle") returns with *lagged* Yen futures returns and categorical calendar seasonal effects. I will be using the following guidelines.

1. Data Preparation (Creating Returns and Lagged Returns and splitting the data into training and testing data)
2. Fitting a Linear Regression Model.
3. Making predictions using the testing data.
4. Out-of-sample performance.
5. In-sample performance.

I will use the results of the linear regression analysis and modeling to answer the following question:

* Does this model perform better or worse on out-of-sample data compared to in-sample data?

## Conclusions of the Time-Series Analysis:

Based on the ARIMA Model and GARCH model, I would feel comfortable buying the Yen now. The ARIMA and GARCH Models are forecasting an increase in momentum over the next 5 days. I do not feel confident in the ARMA Model. The AIC and BIC are too high, especially compared to the ARIMA. The ARMA model is using what seems to be non-stationary data. I was not instructed to use the Augmented Dickey-Fuller model to check if the data was stationary or not. I do not have confidence in the Goodness of Fit in the ARMA model. However, I am more confident in the ARIMA and GARCH models and would use them in my trading until proven wrong. 


## Conclusion of the Linear Regression Analysis:

 After evaluating the results, I have determined that the model needs more information for better accuracy. 
 The error in the out-of-sample data is considerably high at .42 percent and the in-sample data has greater error at .60 percent.
 I do not feel confident in the model as-is and believe more data is needed for better accuracy.
