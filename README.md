# Customer Retention Intelligence — Explainable Churn Prediction

An end-to-end Machine Learning system that predicts customer churn probability and provides explainable insights to support data-driven customer retention strategies.

The project covers the complete ML lifecycle — from exploratory data analysis and preprocessing to model training, threshold optimization, explainability, and deployment through an interactive Streamlit application.

---

## 📌 Project Overview

Customer churn is a critical challenge for subscription-based businesses. Identifying customers who are likely to leave allows companies to take proactive retention actions before the customer churns.

This project builds a machine learning system that uses:

* Customer demographics
* Service usage
* Account information
* Contract details
* Billing information

to estimate the probability that a customer will churn.

The project goes beyond simply building a classification model by incorporating:

* Exploratory Data Analysis (EDA)
* Feature engineering and preprocessing
* Multiple model comparison
* Class imbalance handling
* Classification threshold optimization
* SHAP-based model explainability
* Interactive Streamlit deployment

The final application allows users to enter customer information and receive a **real-time churn probability prediction along with model insights**.

---

## 🚀 Live Demo

### Streamlit Application

🔗 **[Open Live Application](https://customer-retention-intelligence-pm8svys92cdn5fqkmvsboe.streamlit.app/)**

---

# 📊 Dataset

This project uses the **Telco Customer Churn Dataset** available on Kaggle.

**Dataset:**
https://www.kaggle.com/datasets/blastchar/telco-customer-churn

### Dataset Statistics

* **7,043 customer records**
* **21 features**

### Feature Categories

#### 👤 Customer Demographics

* Gender
* Senior Citizen
* Partner
* Dependents

#### 💳 Account Information

* Tenure
* Contract Type
* Paperless Billing
* Payment Method

#### 📡 Services

* Internet Service
* Online Security
* Online Backup
* Device Protection
* Tech Support
* Streaming Services

#### 💰 Billing

* Monthly Charges
* Total Charges

#### 🎯 Target Variable

`Churn`

The objective is to estimate customer churn probability and identify patterns that can support targeted retention strategies.

---

# 🛠️ Tech Stack

| Category             | Technologies  |
| -------------------- | ------------- |
| Programming Language | Python        |
| Data Manipulation    | Pandas, NumPy |
| Machine Learning     | Scikit-learn  |
| Gradient Boosting    | XGBoost       |
| Explainable AI       | SHAP          |
| Visualization        | Matplotlib    |
| Model Serialization  | Joblib        |
| Deployment           | Streamlit     |

---

# ⚙️ Machine Learning Pipeline

The project follows an end-to-end machine learning workflow:

```text
Customer Dataset
       ↓
Exploratory Data Analysis
       ↓
Data Cleaning
       ↓
Feature Engineering
       ↓
Preprocessing
       ↓
Class Imbalance Handling
       ↓
Model Training
       ↓
Model Comparison
       ↓
Threshold Optimization
       ↓
Churn Probability
       ↓
SHAP Explainability
       ↓
Streamlit Deployment
```

---

## 🔢 Numerical Feature Processing

The primary numerical features include:

* Tenure
* Monthly Charges
* Total Charges

### Processing

* Missing value imputation
* Standard scaling

---

## 🔤 Categorical Feature Processing

Categorical features include:

* Gender
* Contract Type
* Internet Service
* Payment Method
* Service-related features

### Processing

* Missing value imputation
* One-hot encoding

All preprocessing is implemented using a **Scikit-learn `ColumnTransformer`**, providing a consistent and reproducible preprocessing pipeline.

---

# 🤖 Machine Learning Models

Three classification models were evaluated.

## 1. Logistic Regression

Used as an interpretable baseline model.

Key characteristics:

* Simple and interpretable
* Strong baseline performance
* High recall for identifying potential churn customers

---

## 2. Random Forest

A tree-based ensemble learning model.

Key characteristics:

* Captures nonlinear relationships
* Robust ensemble approach
* Provides balanced classification performance

---

## 3. XGBoost

A gradient boosting model designed to capture complex patterns in the data.

Key characteristics:

* Gradient boosting architecture
* Handles class imbalance using `scale_pos_weight`
* Uses optimized learning and regularization

---

# 📈 Model Performance

The models were evaluated using ROC-AUC, F1 Score, Precision, and Recall.

| Model               | ROC-AUC | F1 Score | Precision | Recall |
| ------------------- | ------: | -------: | --------: | -----: |
| Logistic Regression |    0.86 |     0.64 |      0.52 |   0.84 |
| Random Forest       |    0.85 |     0.65 |      0.56 |   0.78 |
| XGBoost             |    0.85 |     0.63 |      0.55 |   0.75 |

### Evaluation Metrics

**ROC-AUC**
Measures the model's ability to distinguish between churn and non-churn customers.

**Precision**
Measures how many customers predicted as churn actually churn.

**Recall**
Measures how many actual churn customers are successfully identified.

**F1 Score**
Provides a balance between precision and recall.

For a customer-retention problem, recall is particularly useful because failing to identify a customer who eventually churns can result in a missed retention opportunity.

---

# ⚖️ Classification Threshold Optimization

The default classification threshold of `0.5` is not always optimal for a business problem.

Therefore, different probability thresholds were evaluated to understand the trade-off between:

* Precision
* Recall
* False positives
* False negatives

This allows the business to choose a threshold according to its retention strategy.

For example:

```text
Customer Churn Probability
          ↓
        0.82
          ↓
      HIGH RISK
          ↓
Prioritize for Retention
```

Rather than simply returning a binary prediction, the system provides a **churn probability** that can be used to prioritize customers.

---

# 🔍 Model Explainability with SHAP

Machine learning predictions are more useful when business users can understand why a customer was classified as high risk.

This project uses **SHAP (SHapley Additive Explanations)** to improve model interpretability.

SHAP is used to:

* Explain individual predictions
* Identify important features
* Understand factors contributing to churn
* Analyze global feature importance

### Example Churn Drivers

The analysis identified several important patterns:

* 📉 Low customer tenure → higher churn risk
* 📉 Month-to-month contracts → strong churn driver
* 📈 Higher monthly charges → increased churn probability
* ❌ Lack of security and technical-support services → higher churn risk

---

# 📊 Key Business Insights

## 📌 Contract Type

Customers on **month-to-month contracts** show the highest churn probability.

### Business implication

Businesses can encourage customers to move toward longer-term contracts through targeted incentives.

---

## 📌 Customer Tenure

Customers with shorter tenure are significantly more likely to churn.

### Business implication

New customers should receive stronger onboarding and early-stage retention initiatives.

---

## 📌 Monthly Charges

Higher monthly charges are associated with increased churn.

### Business implication

High-paying customers with elevated churn probability can be prioritized for personalized retention offers.

---

## 📌 Internet Service

Customers using **fiber optic service** show higher churn rates in the dataset.

### Business implication

Service quality, pricing, or customer experience for this segment could be investigated further.

---

## 📌 Value-Added Services

Customers without services such as:

* Online Security
* Tech Support
* Device Protection

are more likely to churn.

### Business implication

Bundling relevant services could potentially improve customer retention.

---

# 💡 Business Recommendations

Based on the model insights, potential retention strategies include:

1. **Encourage long-term contracts**
   Provide incentives for customers to move from month-to-month plans.

2. **Strengthen early customer engagement**
   Focus retention efforts on customers with low tenure.

3. **Target high-value customers**
   Prioritize customers with high monthly charges and high predicted churn probability.

4. **Promote bundled services**
   Offer relevant security, technical support, and protection services.

5. **Use probability-based targeting**
   Instead of treating every customer equally, prioritize customers according to their predicted churn risk.

---

# 🌐 Streamlit Application

The trained machine learning system is deployed through **Streamlit**.

The application allows users to:

* Enter customer information
* Generate churn probability
* Receive a churn prediction
* Understand customer risk
* View model explanations using SHAP

### Application Workflow

```text
Enter Customer Information
          ↓
Preprocess Input
          ↓
ML Model
          ↓
Churn Probability
          ↓
Risk Interpretation
          ↓
Explainable Insights
```

---

# 💻 Run Locally

## 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

## 2. Create a Virtual Environment

### Windows

```bash
python -m venv venv
venv\Scripts\activate
```

### macOS / Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

## 3. Install Dependencies

```bash
pip install -r requirements.txt
```

## 4. Run the Streamlit Application

```bash
streamlit run app.py
```

The application will open at:

```text
http://localhost:8501
```

---

# 📁 Project Structure

```text
customer-retention-intelligence/
│
├── app.py
├── requirements.txt
├── README.md
├── .gitignore
│
├── data/
│   └── telco_customer_churn.csv
│
├── models/
│   └── trained_model.pkl
│
├── notebooks/
│   └── churn_analysis.ipynb
│
└── assets/
    └── ...
```

> The exact structure may differ depending on the current project implementation.

---

# ☁️ Deployment

This project is deployed using **Streamlit Community Cloud**.

### Deployment Workflow

```text
Local Project
     ↓
GitHub Repository
     ↓
Streamlit Community Cloud
     ↓
Live Web Application
```

The repository should contain:

* `app.py`
* `requirements.txt`
* Required model files
* Required supporting files

The Streamlit application uses the dependencies specified in `requirements.txt`.

---

# 🎯 Project Objective

The primary objective of this project is to demonstrate how machine learning can be transformed into a practical business solution.

Rather than focusing only on model accuracy, the project combines:

**Machine Learning + Explainable AI + Business Analytics + Deployment**

This makes the system useful for identifying high-risk customers and supporting data-driven customer-retention decisions.

---

# ⭐ Key Highlights

* End-to-end ML workflow
* Customer churn probability prediction
* Logistic Regression, Random Forest and XGBoost comparison
* Class imbalance handling
* Threshold optimization
* SHAP-based explainability
* Business-focused customer insights
* Interactive Streamlit application
* Deployment-ready architecture

---

# 📜 License

This project is intended for educational, portfolio, and demonstration purposes.
