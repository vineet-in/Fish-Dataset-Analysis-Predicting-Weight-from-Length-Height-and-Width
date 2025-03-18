# Fish Weight Prediction

This repository contains code and analysis to predict the weight of various species of fish based on their physical measurements using linear regression models.

## Dataset Overview

The dataset used contains 159 rows (training samples) and 7 columns:

- **Independent Variables**:
  - `Species`: Species of the fish
  - `Length1`: Vertical length
  - `Length2`: Diagonal length
  - `Length3`: Cross-sectional length
  - `Height`: Height of the fish
  - `Width`: Width of the fish

- **Dependent Variable**:
  - `Weight`: The weight of the fish, which we aim to predict.

## Problem Statement

We aim to estimate the weight of the fish based on its measurements. The dataset contains limited samples, and there are significant multicollinearity issues in some features that we will address during analysis.

## Key Steps in the Analysis

1. **Initial Exploration**: 
   - The dataset is small, with certain species like 'Whitefish' having very few samples. Instead of training models for individual species, we treat all species together due to limited data.

2. **Outlier Removal**:
   - Training data where fish weight is 0 or negative is removed, as these are invalid samples.

3. **Correlation Analysis**:
   - We analyze the correlations between features to understand potential multicollinearity issues that might affect the regression model's reliability.

4. **Multicollinearity Investigation**:
   - We calculate Variance Inflation Factor (VIF) for independent variables to detect multicollinearity.
   - High VIF values indicate strong multicollinearity between variables such as `VerticalLen`, `DiagnolLen`, and `CrossLen`, which can cause unreliable regression coefficients.

5. **Model Building**:
   - We build a linear regression model using the **Ordinary Least Squares (OLS)** algorithm.
   - We split the dataset into training (80%) and testing (20%) sets for model evaluation.

6. **Prediction and Evaluation**:
   - We evaluate the model on test data and observe some issues, particularly with predicting negative weights for smaller fish.

## Results

- The model achieved a prediction accuracy score of **89.6%**.
- One limitation was predicting negative weights for fish with weights below 20 grams, which is unrealistic.

## Conclusion

While the model performs well overall, certain improvements can be made to address issues such as negative weight predictions. One approach could involve reintroducing species-specific models or applying non-linear regression techniques.

## Future Work

- Explore non-linear models to improve predictions for smaller fish weights.
- Investigate alternative techniques to handle multicollinearity, such as **Principal Component Analysis (PCA)** or **Ridge Regression**.
