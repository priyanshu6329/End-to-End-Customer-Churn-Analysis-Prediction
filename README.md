# End-to-End Customer Churn Analysis & Prediction

This project is a complete, end-to-end churn analysis solution for a telecom company. It involves the entire data lifecycle: from raw data ingestion and ETL processing in a SQL database, to building an interactive business intelligence dashboard, and finally, to developing and deploying a machine learning model to predict future customer churn.

---

## 📋 Project Objective

The primary goal is to analyze customer data to identify the key drivers of churn. This analysis is then used to build a predictive model that can identify customers who are at high risk of leaving, allowing the business to take proactive steps to retain them.

---

## 🛠️ Tech Stack

* **Database & ETL:** Microsoft SQL Server
* **Business Intelligence:** Microsoft Power BI
* **Machine Learning:** Python (in a Jupyter Notebook)
* **Key Python Libraries:** Pandas, Scikit-learn, Matplotlib, Seaborn, Joblib

---

## Workflow & Architecture

The project is broken down into four distinct phases, following a standard data analytics workflow.

### **Phase 1: ETL and Data Warehousing (SQL Server)**
The foundation of the project is a robust ETL (Extract, Transform, Load) process built in SQL Server.
1.  **Database Creation**: A new database named `db_Churn` was established to house all project data.
2.  **Data Ingestion**: The raw CSV data was loaded into a staging table (`stg_Churn`) using the SQL Server Import Wizard.
3.  **Data Transformation & Cleaning**: SQL queries were used to explore the data, check for nulls, and handle missing values by replacing them with sensible defaults (e.g., `ISNULL()`).
4.  **Production Table**: The cleaned, transformed data was loaded into a final production table (`prod_Churn`).
5.  **View Creation**: SQL views (`vw_ChurnData`, `vw_JoinData`) were created to provide clean, filtered data sources for Power BI and the machine learning model.

### **Phase 2: Interactive Dashboard (Power BI)**
An executive dashboard was built in Power BI to analyze historical data and identify churn patterns.
1.  **Data Transformation**: Power Query was used to add calculated columns for analysis, such as bucketing customers into Age and Tenure groups. The data model was also enhanced by unpivoting service columns to enable easier filtering.
2.  **DAX Measures**: Key performance indicators (KPIs) were created using DAX, including `Total Customers`, `Total Churn`, and `Churn Rate`.

### **Phase 3: Predictive Modeling (Python & Scikit-learn)**
To predict future churn, a machine learning model was developed.
1.  **Algorithm Selection**: A **Random Forest Classifier** was chosen for this classification task due to its high accuracy and ability to prevent overfitting.
2.  **Model Training & Evaluation**: The model was trained on the historical data and evaluated using a classification report and confusion matrix, achieving **84% accuracy**.
3.  **Feature Importance**: The model's feature importance plot was used to identify the most significant predictors of churn.

### **Phase 4: Predicting & Visualizing New Data**
The trained model was used to score new customers and identify those at high risk of churning.
1.  **Prediction**: The model predicted the churn status for a list of new joiners.
2.  **Visualization of Predictions**: The list of predicted churners was loaded back into Power BI to a dedicated "Churn Prediction" page, providing an actionable list for the marketing team to target with retention campaigns.

## ✨ Dashboard Showcase

Here are snapshots of the final interactive dashboards built in Power BI.

### <p align="center"><i>Historical Churn Analysis</i></p>
This dashboard provides a comprehensive overview of historical churn data, analyzing patterns across demographics, account information, and geography.

![Historical Churn Dashboard](https://github.com/priyanshu6329/End-to-End-Customer-Churn-Analysis-Prediction/blob/main/Dashboard%20w%20tooltip.PNG?raw=true)

### <p align="center"><i>Predicted Churners Dashboard</i></p>
This dashboard page lists the new customers identified by the machine learning model as being at a high risk of churning, providing an actionable list for the marketing team.

![Predicted Churn Dashboard](https://github.com/priyanshu6329/End-to-End-Customer-Churn-Analysis-Prediction/blob/main/Churn%20Prediction.PNG?raw=true)

## ✅ How to Reproduce

To set up and run this project, follow these steps:

1.  **SQL Server Setup**:
    * Create the `db_Churn` database.
    * Run the SQL scripts located in the `/sql_scripts` folder to create the tables and views. You will need to load the initial CSV data into the `stg_Churn` table.
2.  **Python Environment Setup**:
    * Install Anaconda or set up a Python virtual environment.
    * Install the required libraries using the command: `pip install pandas numpy matplotlib seaborn scikit-learn joblib`.
3.  **Run the Jupyter Notebook**:
    * Open the notebook located in the `/notebooks` folder.
    * Update the file paths for the input data and output predictions.
    * Run the cells sequentially to train the model and generate the `Predictions.csv` file.
4.  **Power BI Dashboard**:
    * Open the `.pbix` file located in the `/power_bi` folder.
    * You may need to update the data source connections to point to your local SQL Server instance and the `Predictions.csv` file.
