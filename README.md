# 🏦 Portuguese Bank Marketing Campaigns (2008–2010)  

![Python](https://img.shields.io/badge/Python-3.9-blue?logo=python)  
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-purple?logo=pandas)  
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-green?logo=plotly)  
![Matplotlib](https://img.shields.io/badge/Matplotlib-Visualization-orange)  
![Scikit-Learn](https://img.shields.io/badge/ScikitLearn-ML-yellow?logo=scikitlearn)  
![Tableau](https://img.shields.io/badge/Tableau-Dashboard-blue?logo=tableau)  

---

## ✨ Project Summary  
This project analyzes **Portuguese Bank telemarketing campaign data (2008–2010)** to predict whether a client will subscribe to a **term deposit**.  
The dataset contains **41,188 rows × 20 features** including demographics, macroeconomic indicators, and campaign details.  
Main challenge: **severe class imbalance** → only ~11% of clients subscribed.  

---

## 📖 Context  
- **Business Goal**: Predict whether a client will subscribe to a term deposit (`y = yes/no`).  
- **Dataset Size**: 41,188 rows with 20 features.  
- **Features**:  
  - Client demographics → age, job, marital, education.  
  - Macroeconomic indicators → Euribor, CPI, Employment.  
  - Campaign details → number of contacts, call duration, outcome of previous campaigns.  
- **Source**: UCI ML Repository & Kaggle benchmark dataset.  
- **Challenge**: Severe **class imbalance** (Yes = 11.3%, No = 88.7%).  

---

## 📂 Dataset Distribution  

| Target | Count  | Proportion |
|--------|--------|------------|
| No     | 36,548 | 88.7%      |
| Yes    | 4,640  | 11.3%      |

---

## 🔎 Insights  

### 👥 Age Distribution  
- Majority of clients are **30–50 years old** (economically active group).  

### 📞 Campaign History  
- Most clients had **never been contacted before** (`pdays=999`, `previous=0`).  

### ⏱️ Call Duration  
- Longer calls → higher chance of subscription.  
- ⚠️ Risk of **data leakage** if used blindly.  

### 🌍 Feature Importance (initial)  
- Strongest predictors: **duration, pdays, euribor3m, nr.employed**.  
- Macroeconomic features (`euribor3m`, `emp.var.rate`, `nr.employed`) are highly correlated → feature selection required.  

### 📊 Baseline Model (Logistic Regression)  
- Accuracy ≈ **90%**, but misleading due to imbalance.  
- Recall for “Yes” = **0.20 (20%)** → fails to capture most subscribers.  
- Precision for “Yes” is low → many false positives.  
- ROC AUC = **0.80** → decent discrimination, but can be improved.  

---

## ✅ Recommendations  

### 🔧 Technical (Modeling)  
- Apply `class_weight="balanced"` or resampling (SMOTE, undersampling).  
- Test stronger models → Random Forest, Gradient Boosting, XGBoost.  
- Perform **hyperparameter tuning** and ensemble stacking.  
- Use **Precision-Recall Curve** alongside ROC AUC.  
- Adjust classification threshold (e.g., 0.3) → boost recall for “Yes” class.  

### 📈 Business (Campaign Strategy)  
- Focus on **30–50 age group** → main potential subscribers.  
- Use **customer profiling** (job, marital, education) for targeted campaigns.  
- Avoid **excessive calls** → diminishing returns.  
- Leverage **macroeconomic context** (e.g., low Euribor = more attractive deposits).  
- Treat the model as **decision-support**, not full automation.  

### 🚀 Next Steps  
- Build a **real-time dashboard** for campaign performance.  
- Run **A/B tests**: model-driven vs. random targeting.  
- Include **Customer Lifetime Value (CLV)** for prioritizing high-value clients.  

---

## 📊 Visualizations  

- **Interactive Dashboard (Tableau)**:  
  👉 [Bank Marketing Campaigns Dashboard](https://public.tableau.com/app/profile/dimas.prayoga7117/viz/Visualization_Bank_Marketing/Dashboard1)  
