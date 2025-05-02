# Air Quality Analysis Project: PM2.5 Prediction in NYC

## Overview

This project focuses on analyzing and predicting fine particulate matter (PM2.5) levels across neighborhoods in New York City using data from 2005 to 2022. It leverages regression modeling to identify environmental and temporal drivers of air quality and supports public health initiatives through data-driven insights.

## Objective

**Research Question**: What are the key predictors of PM2.5 levels in NYC neighborhoods, and how accurately can we predict PM2.5 concentrations using advanced regression models?

## Dataset

- **Source**: Publicly available NYC health and environmental data
- **File**: `Air_Quality.csv`
- **Observations**: 18,025 rows
- **Years Covered**: 2005–2022
- **Core Features**:
  - Pollutants: PM2.5, NO₂, Ozone
  - Boiler Emissions: SO₂ density
  - Traffic: Vehicle miles traveled (cars/trucks)
  - Health Outcomes: Asthma ER visits, respiratory deaths
  - Temporal: Year, season
  - Geography: Boroughs, UHF zones, Community Districts

## Methodology

### 1. Exploratory Data Analysis (EDA)
- Distributions, outliers, and trends of pollutants
- Correlations between pollutants and traffic
- Seasonal and neighborhood-level variations

### 2. Data Preparation
- Imputation of missing values
- One-hot encoding of categorical features
- Normalization of numerical features
- Restructuring with pivoted format (Geo, Year, Season as index)

### 3. Model Construction
Three regression models were trained and evaluated:
- **Random Forest Regressor**
- **Gradient Boosting Regressor**
- **Ridge Regression**

### 4. Evaluation Metrics
- Mean Squared Error (MSE)
- R² Score
- 5-fold Cross-Validation

### 5. Results

| Model              | R² Score | MSE   | CV R² (Mean ± Std) |
|-------------------|----------|-------|---------------------|
| Random Forest      | 0.955    | 0.202 | 0.951 ± 0.002       |
| Gradient Boosting  | 0.922    | 0.353 | 0.928 ± 0.004       |
| Ridge Regression   | 0.875    | 0.565 | 0.872 ± 0.006       |

**Best Model**: Random Forest (95.5% variance explained)

## Key Findings

- **Year** was the strongest predictor, reflecting regulatory improvements over time.
- **NO₂** had a strong positive correlation with PM2.5, reflecting shared emission sources.
- **Ozone** was negatively correlated with PM2.5, possibly due to differing seasonal behaviors.
- **Seasonal effects** showed higher PM2.5 in winter.
- **Geographical variation** was modest but present, with urban districts showing higher levels.

## Prediction Results

Predictions on held-out test data showed strong agreement with actual PM2.5 values. Slight underprediction was observed for high-pollution outliers.

## How to Run

1. Install the required libraries:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```

2. Place `Air_Quality.csv` in the working directory.

3. Run the notebook or script containing the analysis pipeline.

## File Structure

```
Air_Quality_Analysis/
├── Air_Quality.csv
├── air_quality_analysis.ipynb
├── README.md
```

## Limitations

- High missingness in Ozone and emissions data reduced their utility.
- Sparse features (boiler emissions, vehicle miles) were excluded from modeling.
- Performance drops slightly when predicting rare extreme pollution events.

## Future Work

- Incorporate weather variables like temperature and humidity.
- Experiment with more sophisticated imputation methods (e.g., KNN, MICE).
- Explore deep learning models to improve prediction during high-PM2.5 episodes.

## Author

Sai Srivatsa  
Data Science Practitioner
