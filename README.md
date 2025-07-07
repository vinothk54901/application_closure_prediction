## 🔍 Use Case: Predicting Application Closure Time

### 🎯 Objective

To **predict the number of days** an application will take to complete the process from **Step 18 to Step 22**.

### 📌 Scenario

- Identify all applications that are **currently at Step 18** (`CURR_STEP = 18`)
- For each of these applications, **predict the number of days** required to reach **Step 22** (final closure)
- This prediction will help stakeholders estimate **closure timelines** and manage expectations

## 🧠 Approach 1: Interval Basis

### 🔄 Data Transformation

- The dataset was transformed so that each step's `LAST_UPDATED_TIMESTAMP` became a separate column.
- This allowed calculation of time intervals between key steps.

### 🎯 Target Variable (DV)

- `step18to22`: Duration in days between Step 18 and Step 22
### 🧮 Independent Variables (IVs)

1. `start_date`: Days between Application Date and Step 1
2. `first_interval`: Days between Step 1 and Step 6
3. `second_interval`: Days between Step 6 and Step 12
4. `third_interval`: Days between Step 12 and Step 18
### 🤖 Model

- **XGBoostRegressor** was used to avoid overfitting
- **Hyperparameter tuning** with GridSearchCV is recommended to improve accuracy

## 🧠 Approach 2: Step Basis

### 🔄 Data Transformation

- Similar transformation as Approach 1: each step's timestamp is a column

### 🎯 Target Variable (DV)

- `step18to22`: Duration in days between Step 18 and Step 22
### 🧮 Independent Variables (IVs)

- `Step1_days`: Days between Application Date and Step 1
- `Step2_days`: Days between Step 1 and Step 2
- `Step3_days`: Days between Step 2 and Step 3
- ...
- `Step18_days`: Days between Step 17 and Step 18
### 🤖 Model

- **XGBoostRegressor** used
