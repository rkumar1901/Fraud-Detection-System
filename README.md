# 🛡️ Fraud Alert System
A system to detect fraudulent credit card transactions using Neural Networks and Decision Trees, backed by a structured SQLite database.
---

## 📌 Problem Statement

Every year, billions of dollars are lost to online payment fraud. This project proposes a **Fraud Alert System** that helps banks and payment service providers analyze transactions **before approving them**, flagging potentially fraudulent activity in real time.

---

## 🎯 Objective

Build a classification model that predicts whether a given financial transaction is **fraudulent or legitimate**, using customer demographics, transaction metadata, and behavioral patterns.

---

## 📂 Dataset

- **Source:** [Kaggle — Credit Card Fraud Detection](https://www.kaggle.com/datasets/kartik2112/fraud-detection?select=fraudTest.csv)
- **Size:** ~1.3 million records, 22 columns
- **Key entities:**
  - 983 unique customers across 494 different job types
  - 700 unique merchants across 14 spending categories
- **Target column:** `is_fraud` (binary: 0 = legitimate, 1 = fraudulent)

---

## 🗄️ Database Design

The raw data is loaded into a **SQLite** database using a **Snowflake Schema** — normalized dimension tables to minimize redundancy.

### Schema Overview

| Table | Type | Description |
|---|---|---|
| `RawTransaction` | Staging | Raw CSV data loaded as-is |
| `City` | Dimension | City, state, and population |
| `Gender` | Dimension | Gender lookup |
| `CustomerJob` | Dimension | Job title lookup |
| `MerchantCategory` | Dimension | Merchant category lookup |
| `Merchant` | Dimension | Merchant details |
| `Customer` | Dimension | Customer profile with FK references |
| `TransactionDetail` | **Fact** | Core transaction records with FK links |

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python |
| Database | SQLite (`sqlite3`) |
| Data Processing | `pandas`, `numpy` |
| Visualization | `seaborn`, `matplotlib` |
| ML / DL | `scikit-learn`, `TensorFlow`, `Keras` |
| Class Imbalance | `imbalanced-learn` (SMOTE, NearMiss) |
| Notebook | Jupyter Notebook |

---

## 🚀 How to Run

### Prerequisites
```bash
pip install pandas numpy scikit-learn imbalanced-learn tensorflow seaborn matplotlib
```

### Steps

1. Download the dataset from [Kaggle](https://www.kaggle.com/datasets/kartik2112/fraud-detection?select=fraudTest.csv) and place `fraudData.csv` in the project root.
2. Open the notebook:
   ```bash
   jupyter notebook Fraud_Detection_Project.ipynb
   ```
3. Run all cells in order:
   - **Section 1** — Creates and populates the SQLite database (`fraud_data.db`)
   - **Section 2** — Runs EDA, feature engineering, and model training
   - **Results** — Outputs confusion matrix, accuracy, and sensitivity scores

---

## 🔮 Future Improvements

- Incorporate additional transaction-level features such as **Card Present Indicator**, **POS Terminal Mode**, and **Transaction Type** for richer signal
- Build an **automated data pipeline** for real-time data ingestion, model scoring, and alerting
- Deploy the model as a **REST API** or cloud-based microservice for integration with payment systems
- Evaluate additional models such as **XGBoost** or **Random Forest** for further accuracy gains

---

## 📄 License

This project is open source and available for academic and educational use.
