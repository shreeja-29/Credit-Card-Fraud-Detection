# 🚨 Credit Card Fraud Detection

## Overview

The **Credit Card Fraud Detection** project aims to build an efficient classification model that identifies fraudulent credit card transactions. Leveraging advanced machine learning techniques, this project focuses on minimizing false positives while ensuring high overall accuracy. The dataset used includes anonymized PCA-transformed features (V1–V28), transaction time, transaction amount, and a class label indicating whether a transaction is fraudulent.

---

## Objectives

- Develop a robust fraud detection model using a Random Forest Classifier.
- Engineer meaningful features (e.g., converting raw time into transaction hour, logarithmic transformation of transaction amount) for better insight into spending patterns.
- Address class imbalance through oversampling (using SMOTE) to boost detection of rare fraudulent cases.
- Evaluate the model thoroughly using classification reports, confusion matrices, and ROC AUC scores.
- Visualize the evaluation metrics and feature importances for transparent insights.

---

## Approach & Methodology

### 1. Data Loading
- **Dataset:** The dataset includes columns such as `Time`, `V1` to `V28`, `Amount`, and `Class`.
- **Exploration:** We start by viewing the dataset's structure and class distribution to understand the imbalance between genuine and fraudulent transactions.

### 2. Preprocessing & Feature Engineering
- **Time Feature Transformation:**  
  Convert the raw `Time` (seconds since a reference point) into a more interpretable `TransactionHour` to capture diurnal patterns.
- **Amount Transformation:**  
  Apply a logarithmic transformation to the `Amount` field (using `np.log1p`) to better capture spending behavior across a wide range.
- **Handling Missing Values:**  
  Although the dataset is typically clean, any missing numeric values are imputed with their median.
- **Categorical and PCA Features:**  
  In this case, the principal components (V1–V28) are already generated. We keep these along with engineered time and amount features.

### 3. Handling Class Imbalance
- **SMOTE:**  
  Given the severe imbalance in the fraud class, Synthetic Minority Oversampling Technique (SMOTE) is applied on the training data to create a balanced dataset, thus ensuring the model does not overlook rare fraudulent transactions.

### 4. Model Selection & Training
- **Algorithm:**  
  A **Random Forest Classifier** is chosen for its robustness, interpretability, and strong performance in detecting complex patterns.
- **Training:**  
  The model is trained on scaled features (standardized using `StandardScaler`) from the balanced training set.

### 5. Evaluation & Analysis
- **Performance Metrics:**  
  - **Classification Report:** Precision, recall, and F1-score per class.
  - **Confusion Matrix:** Visualizes true vs. predicted labels to understand misclassification.
  - **ROC AUC:** Provides insight into the model’s discriminatory ability between fraudulent and non-fraudulent transactions.
- **Visualizations:**  
  - ROC Curve to illustrate trade-offs between true positive and false positive rates.
  - Feature Importance Chart to highlight the most influential features in the model.



## How to Run the Project

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/shreeja-29/Credit-Card-Fraud-Detection.git
   cd Credit-Card-Fraud-Detection
   ```

2. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Place the Dataset:**
   Ensure that `creditcard.csv` is located in the `data/` folder.
      https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud
4. **Run the Code:**
   - To run the complete fraud detection pipeline, execute:
     ```bash
     python src/credit_card_fraud_detection.py
     ```
   - Alternatively, open and run the Jupyter Notebook in the `notebooks/` folder for an interactive session.

---

## Evaluation Results & Insights

Upon running the pipeline, you will obtain:
- **Detailed Model Performance:**  
  Including precision, recall, F1-score, and ROC AUC metrics.
- **Visual Insights:**  
  Confusion Matrix heatmaps and ROC curves to better interpret model outcomes.
- **Feature Analysis:**  
  A feature importance plot that indicates which features (such as engineered `TransactionHour` or `LogAmount`) play a crucial role in fraud detection.

These outcomes help in refining the model and support actionable insights to improve credit card fraud detection strategies.
