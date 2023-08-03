# Store_Sales_Forecasting

# Overview
One of the most important tasks for any retail store company is to analyze the performance of its stores. The main challenge faced by any retail store is predicting in advance the sales and inventory required at each store to avoid over-stocking and under-stocking. This helps the business to provide the best customer experience and avoid getting into losses, thus ensuring the store is sustainable for operation.

Rossmann operates over 3,000 drug stores in 7 European countries. We are tasked with predicting their daily sales for up to six weeks in advance. Store sales are influenced by many factors, including promotions, competition, school and state holidays, seasonality, and locality. 

# Files
We are provided with historical sales data for 1,115 Rossmann stores. 
•	train.csv - historical data including Sales
•	test.csv - historical data excluding Sales
•	sample_submission.csv - a sample submission file in the correct format
•	store.csv - supplemental information about the stores

# Approach
We’ll start by exploring the data set followed by dealing with missing values and doing some feature engineering. Then, we’ll build some predictive models to predict the sales using time series forecasting models such as ARIMA and Prophet.

# Evaluation Metrics
There are two popular metrics used in measuring the performance of regression (continuous variable) models i.e MAE & RMSE.

Mean Absolute Error (MAE): It is the average of the absolute difference between the predicted values and observed values.
Root Mean Square Error (RMSE): It is the square root of the average of squared differences between the predicted values and observed values.

MAE is easier to understand and interpret but RMSE works well in situations where large errors are undesirable. This is because the errors are squared before they are averaged, thus penalizing large errors. In our case, RMSE suits well because we want to predict the sales with minimum error (i.e penalize high errors) so that inventory can be managed properly.

So, we’ll choose RMSE as a metric to measure the performance of our models.

# Libraries Used
Numpy, pandas, seaborn, statsmodels, ARIMA, Prophet, sklearn

# Results
We will use the Root Mean Squared Error (RMSE) to evaluate and validate the performance of various models. 

# Model Comparison & Selection
a) We can see from the above table that SARIMA performs the best followed by Prophet.

b) It makes sense because SARIMA is designed specifically for seasonal time series data.

c) Prophet is a good choice for producing quick forecasts as it doesn’t require strong technical skills. It is easy to implement at scale. The reason for its poor performance here is probably because of a lack of data. It works best with time series that have strong seasonal effects and several seasons of historical data. Prophet is robust to missing data and shifts in the trend, and typically handles outliers well.

Based on the above analysis, we’ll choose ARIMA as our final model to predict the sales because it gives us the least RMSE and is well suited to our needs of predicting time series seasonal data. We chose ARIMA(1, 1, 1)x(0, 1, 1, 12)12 as the final parameter combination with AIC of 1806.29 and RMSE of 739.06.

# Conclusion

# Reflection
•	The most interesting thing about the data was that the category of stores having the highest sales didn’t have the highest sale per customer. It might be because those stores sell small items, which are needed on a daily basis.

•	Another interesting thing was that running a promotion for the second time didn’t help in increasing sales. It is probably because customers already purchased whatever they wanted during the first promotional sale.

# Acknowledgments

https://www.kaggle.com/c/rossmann-store-sales

https://machinelearningmastery.com/arima-for-time-series-forecasting-with-python/

https://www.digitalocean.com/community/tutorials/a-guide-to-time-series-forecasting-with-arima-in-python-3

https://facebook.github.io/prophet/docs/quick_start.html

