# NYC Taxi Demand Analysis and Forecasting

## Project Overview
This project analyses real NYC yellow taxi trip data and builds a simple forecasting model to predict hourly taxi demand.

The main goal of the project is to understand how taxi demand changes over time and to test whether a machine learning model can predict the number of taxi trips in the next hour better than a baseline.

This project was done as part of my data science learning journey using real public data.

---

## Dataset
The dataset used in this project is the **NYC Yellow Taxi Trip Record Data**.

It contains real trip-level records such as:
- pickup and dropoff date/time
- trip distance
- passenger count
- fare amount
- pickup and dropoff locations

For this project, I used one month of yellow taxi data and then converted the trip-level records into **hourly demand data**.

---

## Project Goal
The main questions I wanted to answer were:

- At what times of day is taxi demand highest?
- How does taxi demand change across weekdays and weekends?
- Can I build a model that predicts hourly taxi demand better than a simple baseline?
- What features are useful for forecasting demand?

---

## Tools Used
- Python
- Jupyter Notebook
- pandas
- numpy
- matplotlib
- scikit-learn

---

## Workflow

### 1. Data Loading
I loaded the raw NYC yellow taxi trip data into pandas.

### 2. Data Cleaning
I cleaned the dataset by:
- removing missing pickup/dropoff times
- removing trips with non-positive duration
- removing clearly unreasonable trips
- removing negative fare or distance values
- removing duplicate rows

This step was important because real-world datasets are often messy, and machine learning models need clean input data.

### 3. Feature Engineering
I created new features from the pickup datetime, such as:
- hour of day
- day of week
- weekend indicator

Then I converted the trip-level data into an **hourly time series**, where each row represents the number of trips in one hour.

After that, I created forecasting features such as:
- lag features (`lag_1`, `lag_2`, `lag_24`, etc.)
- rolling averages
- rolling standard deviations
- cyclical time features using sine and cosine

These features help the model learn patterns like rush hours, daily cycles, and weekly cycles.

### 4. Baseline Forecast
Before training a real model, I created a **naive baseline**.

This baseline predicts the next hour’s taxi demand using the previous hour’s demand.

This gives a simple reference point and helps answer the question:
**Is the machine learning model actually better than a very simple guess?**

### 5. Model Training
I trained a **Linear Regression** model to predict hourly taxi demand.

The model used lag features, rolling statistics, and time-based features as inputs.

### 6. Model Evaluation
I evaluated the forecasting models using:
- **MAE (Mean Absolute Error)**
- **RMSE (Root Mean Squared Error)**

These metrics show how far the predictions are from the true demand values.

### 7. Visualization
I created plots to better understand the data and the model results, including:
- trips by hour of day
- trips by day of week
- hourly demand over time
- actual vs predicted demand

---

## Models Used

### 1. Naive Baseline

### 2. Linear Regression

### 3. Hist Gradient Boosting Regression
---

## Results

### Baseline Model
- **MAE:** 945.75
- **RMSE:** 1396.45

### Linear Regression Model
- **MAE:** 473.34
- **RMSE:** 828.29

### Hist Gradient Boosting Regression
- **MAE:** 410.05
- **RMSE:** 832.24

### Interpretation
The linear regression model performed much better than the naive baseline, and Hist regression model performed better than linear regression model on MAE, but did not improve the RMSE.


This means the machine learning model was able to learn useful demand patterns from the data and make better forecasts than simply copying the previous hour.

However, the error is still fairly large, which suggests that hourly taxi demand is a difficult prediction problem. Demand can change because of rush hours, weekends, weather, events, and other factors that are not fully captured by a simple linear model.

---

## What I Learned
This project taught me several important data science ideas:

- real datasets need cleaning before modeling
- time-based data often needs feature engineering
- forecasting is different from ordinary machine learning because time order matters
- a baseline model is very important for comparison
- better features can improve model performance
- even a simple model can beat a naive baseline if the data is prepared well

---

## Why This Project Matters
This project is useful for my portfolio because it demonstrates:
- working with a real public dataset
- cleaning messy real-world data
- feature engineering
- time series aggregation
- forecasting
- model evaluation
- interpretation of results

It shows that I can go beyond toy datasets and build a complete data science workflow from raw data to final results.

---

## Files in This Repository
- `notebooks/nyc_taxi_demand_analysis.ipynb` — main notebook
- `outputs/model_results.csv` — model comparison results
- `outputs/actual_vs_predicted.csv` — prediction output
- `README.md` — project summary

---

## How to Run This Project

### 1. Clone the repository
```bash
git clone https://github.com/vishalyadav1729/nyc-taxi-demand-analysis.git
