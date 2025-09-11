# Car Price Prediction

## Overview
This project predicts car prices based on various specifications using Machine Learning techniques. The analysis includes data cleaning, exploratory data analysis (EDA), feature engineering, model training, hyperparameter tuning, and evaluation.  

The goal is to build a predictive model that can estimate car prices accurately given key features.

---

## Dataset

**Features include:**
- **Categorical:** `fueltype`, `aspiration`, `doornumber`, `carbody`, `drivewheel`, `enginelocation`, `enginetype`, `cylindernumber`, `fuelsystem`  
- **Numerical:** `wheelbase`, `carlength`, `carwidth`, `carheight`, `curbweight`, `enginesize`, `boreratio`, `stroke`, `compressionratio`, `horsepower`, `peakrpm`, `citympg`, `highwaympg`, `price`  

---

## Feature Engineering
- Created **feature ratios** to capture meaningful relationships:  
  - `length_width_ratio = carlength / carwidth`  
  - `weight_power_ratio = curbweight / horsepower`  
  - `engine_per_cylinder = enginesize / cylindernumber`  
  - `weight_engine_ratio = curbweight / enginesize`  
  - `power_engine_ratio = horsepower / enginesize`  

- Encoded categorical variables using One-Hot or Label Encoding.  
- Scaled numerical features with `StandardScaler`.  

---

## Exploratory Data Analysis (EDA)
- Visualized relationships between features and price using scatter plots, boxplots, and countplots.  
- Identified strong positive correlations with price: `enginesize`, `curbweight`, `horsepower`, `carwidth`.  
- Found strong negative correlations with fuel efficiency features: `citympg`, `highwaympg`.  
- Addressed multicollinearity by creating feature ratios and dropping redundant features.  

---

## Modeling
**Models used:**
1. Linear Regression (baseline)  
   - R² ≈ 0.905, RMSE ≈ 2246  
2. Ridge Regression (with GridSearchCV)  
   - Best alpha = 10.0  
   - R² ≈ 0.931, RMSE ≈ 1911  
3. Random Forest Regressor (with GridSearchCV)  
   - Best params: `n_estimators=100`, `max_depth=None`, `min_samples_split=2`  
   - R² ≈ 0.958, RMSE ≈ 1496  

**Observations:**  
- Random Forest gives the most accurate predictions and handles non-linear relationships well.  
- Ridge Regression improves linear performance using regularization.  
- Linear Regression serves as a good baseline but less reliable for extreme values.  

---

## Visualization
- Scatter plots and residual plots confirm model performance and show differences between models.  
- Used a consistent **Seaborn theme and color palette** for all visualizations.  

---

## How to Use
1. Clone the repository:  
```bash
git clone https://github.com/rahmaayman1/Car-Price-Prediction.git
