# Bike Rental Demand Prediction

This repository contains the code and analysis for predicting bike rental demand using a multiple linear regression model. The goal is to understand the factors influencing bike rentals and to build a predictive model with high accuracy.

## Dataset

The dataset contains daily records of bike rentals and includes features such as temperature, humidity, wind speed, season, and weather conditions.

## Selected Features

The following features were selected for the final model:
- Year (`yr`)
- Apparent temperature (`atemp`)
- Humidity (`hum`)
- Wind speed (`windspeed`)
- Season (Spring, Winter)
- Weather situation (Light Rain, Mist)
- Month (July, November)

## Model Performance

### Training Set
- **R-squared**: 0.826
- **Adjusted R-squared**: 0.823
- **F-statistic**: 237.8 (p-value: 7.12e-183)

### Test Set
- **R-squared**: 0.822
- **Adjusted R-squared**: 0.814

### Feature Coefficients

| Feature              | Coefficient | P-value   |
|----------------------|-------------|-----------|
| const                | 4552.9511   | 0.000     |
| yr                   | 980.1396    | 0.000     |
| atemp                | 913.4594    | 0.000     |
| hum                  | -205.2597   | 0.000     |
| windspeed            | -171.8283   | 0.000     |
| season_spring        | -531.8970   | 0.000     |
| season_winter        | -296.9168   | 0.000     |
| weathersit_light_rain| 268.4140    | 0.000     |
| weathersit_mist      | -216.4486   | 0.000     |
| mnth_Jul             | -188.4348   | 0.000     |
| mnth_Nov             | -161.1723   | 0.000     |

### Multicollinearity Check

All VIF values are below 5, indicating no significant multicollinearity.

## Residual Analysis

- **Omnibus**: 70.060
- **Jarque-Bera**: 137.364
- **Durbin-Watson**: 2.016

The residual analysis suggests that the model performs well, though there are minor deviations from normality and potential autocorrelation.

## Conclusion
### Model Performance

1. **High R-squared Value**:
   - The R-squared value of 0.826 indicates that the model explains approximately 82.6% of the variance in the target variable (`cnt`). This suggests a strong model performance.
   - The adjusted R-squared value of 0.823 is slightly lower but still indicates a good fit, taking into account the number of predictors in the model.
2. **Statistical Significance**:
   - The F-statistic of 237.8 and the associated p-value (7.12e-183) indicate that the model as a whole is statistically significant.
### Feature Significance

1. **Coefficients**:
   - The coefficients for the features indicate the direction and magnitude of the relationship between each feature and the target variable (`cnt`). For example, the positive coefficient for `yr` (980.1396) suggests that bike rentals have increased over the years.
   - `atemp` (913.4594) has a strong positive impact on bike rentals, indicating that higher apparent temperature is associated with more rentals.
   - `hum` (-205.2597) and `windspeed` (-171.8283) have negative coefficients, indicating that higher humidity and wind speed are associated with fewer bike rentals.
2. **Seasonal and Weather Effects**:
   - `season_spring` (-531.8970) and `season_winter` (-296.9168) have significant negative effects compared to the base season (presumably summer).
   - `weathersit_light_rain` (268.4140) positively influences bike rentals compared to clear weather, while `weathersit_mist` (-216.4486) has a negative effect.
3. **Monthly Effects**:
   - `mnth_Jul` (-188.4348) and `mnth_Nov` (-161.1723) both have negative coefficients, suggesting fewer rentals in July and November compared to the base month.

### Multicollinearity

- The Variance Inflation Factor (VIF) values for all features are below 5, indicating that multicollinearity is not a concern in this model.

### Residual Analysis

- The Omnibus, Jarque-Bera, and Durbin-Watson statistics suggest that the residuals are not perfectly normally distributed and there might be some autocorrelation, but overall, the model diagnostics are acceptable for this type of regression analysis.

### Test Set Performance

- The R-squared on the test set is 0.822, and the adjusted R-squared is 0.814, indicating that the model generalizes well to unseen data and retains high explanatory power.

## How to Use

1. Clone the repository:
   ```
   git clone https://github.com/phanirajcm/bike-rental-demand-prediction
   ```
2. Install the required packages:
   ```
   pip install -r requirements.txt
   ```
3. Run the analysis:
   ```
   python analysis.py
   ```

