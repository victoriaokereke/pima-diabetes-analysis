# Pima Indians Diabetes Classification: Data Analysis and Machine Learning

## Overview

This project investigates the development of a machine learning classification workflow for predicting diabetes outcomes using the Pima Indians Diabetes dataset.

The analysis focuses on handling challenges commonly encountered in clinical datasets, including missing values, feature quality issues, model selection, hyperparameter optimization, and decision threshold adjustment.

The primary objective is to maximize identification of diabetic patients by prioritizing recall while maintaining acceptable precision.

---

## Dataset

The dataset contains medical diagnostic measurements from 768 female patients of Pima Indian heritage.

Features include:

- Glucose concentration
- Blood pressure
- Skin thickness
- Insulin
- BMI
- Diabetes pedigree function
- Age

The target variable is:

- Outcome (0 = non-diabetic, 1 = diabetic)

---

## Project Objectives

This project aims to:

1. Perform exploratory data analysis to understand feature distributions and relationships with diabetes outcome.
2. Identify and handle invalid missing values within clinical variables.
3. Compare missing value imputation strategies using masked Mean Absolute Error (MAE).
4. Evaluate the impact of different imputation approaches on downstream machine learning performance.
5. Compare multiple classification algorithms using cross-validation.
6. Optimize model hyperparameters based on recall.
7. Adjust classification thresholds to improve detection of diabetic cases.
8. Evaluate the final model on an unseen test dataset.

---

## Methodology

The analysis workflow consisted of:

### 1. Exploratory Data Analysis

- Investigated feature distributions
- Analysed relationships between predictors and diabetes outcome
- Identified abnormal zero values representing missing measurements

### 2. Missing Data Handling

Two imputation strategies were evaluated:

- K-Nearest Neighbour Imputation (KNNImputer)
- Iterative Imputation (MICE)

Imputation performance was assessed via artificial masking of the dataset and Mean Absolute Error (MAE).

### 3. Model Development

Baseline models evaluated were:

- Logistic Regression
- Decision Tree
- Random Forest
- K-Nearest Neighbours
- XGBoost
- Calibrated Support Vector Machine

Model Performance was evaluated using:

- ROC-AUC
- Recall
- Precision
- F1-score

### 4. Model Optimization

The strongest baseline models were tuned using GridSearchCV.

Since the objective was healthcare screening, recall was prioritized to reduce false negatives.

Threshold tuning was then performed to identify an appropriate balance between recall and precision.

---

## Final Model Performance

Final model:

| Component | Selection |
|---|---|
| Model | CalibratedClassifierCV |
| Imputer | KNNImputer |
| Threshold | 0.25 |

Test performance:

| Metric | Score |
|---|---:|
| Accuracy | 0.649 |
| Precision | 0.500 |
| Recall | 0.796 |
| F1-score | 0.614 |
| ROC-AUC | 0.786 |

The selected threshold increased recall, allowing more diabetic cases to be identified with a trade-off of additional false positives.

## Repository Structure.

```test
pima-diabetes-analysis/
│
├── data/
│ └── diabetes_cleaned.csv
│
├── notebooks/
│ ├── pima_diabetes_eda.ipynb
│ └── pima_diabetes_modelling.ipynb
│
├── .gitignore
├── requirements.txt
└── README.md
```

---

## Getting Started

### Requirements

Python 3.9+

### Installation

```bash
git clone https://github.com/victoriaokereke/pima-diabetes-analysis.git
cd pima-diabetes-analysis
pip install -r requirements.txt
```
---