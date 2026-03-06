#  End-to-End ML System with Deployment
### Production-Based Fraud Detection System

A production-ready, end-to-end machine learning system for detecting financial fraud — from raw data to a live REST API deployed on AWS.


## 🏗️ Architecture

```
Raw Data (6.3M rows)
        ↓
Exploratory Data Analysis (7 visualizations)
        ↓
Feature Engineering (27 new features)
        ↓
Model Training (XGBoost GPU + Random Forest)
        ↓
MLflow Experiment Tracking
        ↓
FastAPI Prediction Server
        ↓
Docker Container
        ↓
GitHub Actions CI/CD
        ↓
AWS ECS (Production)
```

---

## 📁 Project Structure

```
├── app/
│   └── main.py                          # FastAPI prediction server
├── Dataset/
│   ├── fraud_data.csv                   # Raw data (git-ignored)
│   └── transactions_engineered.parquet  # Engineered features (git-ignored)
├── EDA/
│   ├── eda.ipynb                        # Exploratory analysis notebook
│   └── plot_*.png                       # 7 EDA visualizations
├── evaluation/
│   ├── model_evaluation.py              # Evaluation script
│   └── plots/                           # ROC, PR curve, confusion matrix
├── feature_engineering/
│   └── feature_engineering.py          # 27 engineered features
├── model_training/
│   ├── model_training.py               # XGBoost + Random Forest training
│   └── log_mlflow.py                   # MLflow experiment logging
├── models/
│   ├── xgboost.pkl                     # Trained XGBoost model
│   ├── random_forest.pkl               # Trained Random Forest model
│   └── best_model.pkl                  # Best model bundle
├── .github/
│   └── workflows/
│       └── deploy.yml                  # GitHub Actions CI/CD pipeline
├── Dockerfile                          # Container definition
├── requirements-docker.txt             # Production dependencies
└── requirements.txt                    # Full dependencies
```

## ⚙️ Feature Engineering (27 New Features)

| Block | Features |
|-------|----------|
| Balance Integrity | `errorBalanceOrig`, `errorBalanceDest`, `abs_errorBalanceOrig`, `abs_errorBalanceDest` |
| Zero Balance Flags | `isOrigZeroAfter`, `isOrigZeroBefore`, `isDestZeroBefore`, `isDestZeroAfter`, `suspiciousWipe` |
| Ratio Features | `amountToOldBalanceOrig`, `amountToOldBalanceDest`, `origBalanceChangeRatio` |
| Type Encoding | `isTransfer`, `isCashOut`, `isHighRiskType` + 5 one-hot columns |
| Log Transforms | `log_amount`, `log_oldbalanceOrg`, `log_newbalanceOrig`, `log_oldbalanceDest`, `log_newbalanceDest`, `amountTier` |
| Account Velocity | `origAcctFrequency`, `destAcctFrequency`, `isMuleDestCandidate` |
| Time Features | `hour_of_day`, `day_of_month`, `isNightTime` |

--- 

---

## 🖥️ Web App Preview

<!-- Add your screenshot here:
1. Take a screenshot of your running API (http://localhost:8000/docs)
2. Save it as preview.png
3. Create an images/ folder in your project
4. Put preview.png inside images/
5. Push to GitHub — the image will appear here automatically -->

![Web App Preview](web_preview.png)

---
