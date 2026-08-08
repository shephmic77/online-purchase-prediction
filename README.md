# Predicting Online Purchase Intention and Discovering Shopper Segments

A data science project analyzing online shopping behavior using supervised classification and unsupervised clustering.

This project was completed for STAT 380 at Penn State. The goal was to answer two questions:

1. Can browsing behavior predict whether an online shopping session will end in a purchase?
2. Are there distinct behavioral groups among online shopping sessions when purchase outcome is not used?

## Dataset

The project uses the UCI Online Shoppers Purchasing Intention Dataset, which contains 12,330 online shopping sessions and 18 analysis variables.

The response variable is `Revenue`, which indicates whether a session resulted in a purchase. About 15.5% of sessions resulted in a purchase, creating a class imbalance that was considered during model evaluation.

The dataset is imported directly from the UCI Machine Learning Repository by the R Markdown file.

## Methods

The analysis includes:

- Exploratory data analysis and visualization
- Data quality checks and preprocessing
- Training, validation, and test splitting
- Logistic regression
- K-nearest neighbors (KNN)
- 10-fold cross-validation
- ROC and AUC analysis
- Confusion matrix evaluation
- K-means clustering

Categorical variables were treated as factors for logistic regression and one-hot encoded for KNN. Numeric predictors used by distance-based methods were standardized using values calculated from the training data.

## Model Results

Logistic regression and KNN were compared using validation performance.

The final selected model was logistic regression with a probability threshold of 0.12.

### Final Test Performance

| Metric | Result |
| --- | ---: |
| Accuracy | 78.4% |
| Sensitivity | 86.8% |
| Specificity | 76.9% |
| Precision | 40.8% |
| Balanced Accuracy | 81.8% |
| AUC | 0.91 |

The lower probability threshold improved the model's ability to identify purchasing sessions, which was important because purchases represented the minority class.

## Shopper Segmentation

K-means clustering was performed separately from the supervised prediction analysis.

`Revenue` was removed before selecting the clustering variables or number of clusters. The analysis selected four behavioral segments:

1. **Quick-exit sessions** – high bounce and exit rates
2. **Special-day visitors** – unusually high SpecialDay values
3. **Intensive product browsers** – high page counts and browsing durations
4. **Typical browsing sessions** – the largest group, with behavior closer to the overall average

Purchase outcomes were only examined after the clusters were finalized.

## Repository Structure

```text
analysis/
    online_purchase_analysis.Rmd

assignment/
    project_instructions.pdf

report/
    online_purchase_report.pdf
- `analysis/` contains the reproducible R Markdown analysis.
- `assignment/` contains the original project instructions and requirements.
- `report/` contains the completed project report.

## Reproducibility

The R Markdown file imports the dataset directly from UCI and reproduces the analysis, tables, figures, and model results.

Random operations use a fixed seed of `380`.

## Tools and Techniques

R, tidyverse, ggplot2, logistic regression, K-nearest neighbors, cross-validation, ROC/AUC analysis, K-means clustering, data preprocessing, and data visualization.

## Author

Michael Shepherd  
Data Science, Penn State University
