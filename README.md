Lab 4: Regression Analysis with Regularization Techniques

Purpose

This lab explores multiple regression techniques and regularization methods using the Diabetes Dataset from sklearn. The objective is to implement and compare Linear Regression, Multiple Regression, Polynomial Regression, Ridge Regression, and Lasso Regression models to predict disease progression based on health measurements.

Dataset

Source: sklearn.datasets Diabetes Dataset
Size: 442 samples, 10 features
Target: Disease progression score (25-346)
Features: age, sex, bmi, bp, s1, s2, s3, s4, s5, s6
Data Quality: No missing values detected

Models Implemented

1. Simple Linear Regression
Feature Used: BMI (highest correlation with target: 0.586)
Performance: R² = 0.233, RMSE = 63.732

2. Multiple Linear Regression
Features Used: All 10 features
Performance: R² = 0.453, RMSE = 53.853
Most Important Feature: s1 (coefficient: -931.49)

3. Polynomial Regression
Degree 2: R² = 0.416, RMSE = 55.642
Degree 3: R² = -14.561, RMSE = 287.134 (severe overfitting)
Degree 4: R² = -26.728, RMSE = 383.285 (severe overfitting)

4. Ridge Regression
Best Alpha: 0.1
Performance: R² = 0.461, RMSE = 53.446
Effect: Reduced coefficient magnitudes while retaining all features

5. Lasso Regression
Best Alpha: 0.1
Performance: R² = 0.472, RMSE = 52.898
Effect: Selected 7 out of 10 features (eliminated age, s2, s4)

Key Insights

Model Performance Ranking
1. Lasso (α=0.1) - Best overall performance (R² = 0.472, RMSE = 52.898)
2. Ridge (α=0.1) - Second best (R² = 0.461, RMSE = 53.446)
3. Multiple Linear - Baseline comparison (R² = 0.453, RMSE = 53.853)
4. Polynomial (degree 2) - Moderate improvement (R² = 0.416, RMSE = 55.642)
5. Simple Linear - Limited single-feature performance (R² = 0.233, RMSE = 63.732)

Overfitting Observations
Polynomial degrees 3 and 4 showed severe overfitting with negative R² scores
Higher polynomial degrees dramatically increased prediction errors
Regularization successfully prevented overfitting compared to high-degree polynomials

Regularization Effects
Ridge Regression: Shrunk coefficients but retained all features
Lasso Regression: Performed automatic feature selection, eliminating 3 features
Alpha Parameter: Lower values (0.1) performed better than higher regularization strengths

Feature Importance
Most Influential: s1 (serum measurement) with highest absolute coefficient
Lasso Selection: Retained bmi, bp, sex, s1, s3, s5, s6
Eliminated Features: age, s2, s4 (set to zero by Lasso)

Challenges and Decisions

Challenge 1: Feature Selection for Simple Regression
Issue: Choosing the best single feature for simple linear regression
Solution: Selected BMI based on highest correlation with target variable (0.586)

Challenge 2: Polynomial Degree Selection
Issue: Determining optimal polynomial degree
Decision: Tested degrees 2-4 to demonstrate overfitting progression
Outcome: Degree 2 provided reasonable balance, higher degrees severely overfit

Challenge 3: Regularization Parameter Tuning
Issue: Selecting appropriate alpha values for Ridge and Lasso
Decision: Tested alpha values [0.1, 1.0, 10.0, 100.0]
Finding: Lower regularization (α=0.1) performed best for both methods

Challenge 4: Model Evaluation Strategy
Decision: Used consistent train-test split (80-20) across all models
Metrics: Employed multiple evaluation metrics (MAE, MSE, RMSE, R²) for comprehensive assessment
Visualization: Created comparison plots to illustrate performance differences

Conclusions

1. Multiple regression significantly outperformed single-feature regression, improving R² from 0.233 to 0.453
2. Regularization provided the best performance, with Lasso achieving the highest R² (0.472)
3. Polynomial regression demonstrated clear overfitting beyond degree 2
4. Feature selection through Lasso identified 7 key features while maintaining performance
5. The diabetes dataset responds well to regularized linear models rather than complex polynomial approaches

The analysis demonstrates that while multiple features improve prediction accuracy, careful regularization and feature selection are crucial for optimal model performance.
