# Retail Sales Data Cleaning & Exploratory Analysis

An end-to-end data analysis project focusing on raw retail transaction data. This repository contains the complete pipeline for data cleaning, handling missing values, custom IQR outlier detection, and statistical univariate visualization, accompanied by an interactive Tableau dashboard.

---

## Live Tableau Dashboard
View the interactive visual insights on Tableau Public:
**[View Interactive Tableau Dashboard](https://public.tableau.com/views/SalesRetailAnalysisDashboard_17845547813660/Customers?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**

---

## Project Overview
The objective of this project is to clean, transform, and analyze a dataset consisting of 4,200 retail sales orders across multiple product categories, customer demographics, and regions.

### Key Highlights:
- **Data Validation & Cleaning:** Handled missing age attributes and corrected invalid customer entries (<18 years old).
- **Outlier Analysis:** Implemented an IQR (Interquartile Range) detection algorithm to identify and clean extreme quantity anomalies (`quantity == 999`).
- **Custom Visual Styling:** Built a global dark-theme layout using Matplotlib and Seaborn for consistent data presentation.

---

## Tech Stack & Libraries
- **Language:** Python
- **Data Manipulation:** `pandas`, `numpy`
- **Visualization:** `matplotlib`, `seaborn`
- **BI & Dashboarding:** Tableau Public
- **Environment:** Google Colab / Jupyter Notebooks

---

## Data Cleaning & Preprocessing Pipeline

1. **Duplicate Verification:** Checked primary keys (`order_id`) to ensure unique transactional records.
2. **Type Casting:** Converted string dates to native Python `datetime` formats for time-series analysis.
3. **Age Imputation:**
   - Identified zero and invalid age records (`age < 18`).
   - Imputed invalid records using the overall mean customer age ($~34$ years).
4. **Outlier Treatment (IQR Method):**
   - Implemented custom function using the standard rule:
     ```python
     IQR = Q3 - Q1
     Lower Bound = Q1 - 1.5 * IQR
     Upper Bound = Q3 + 1.5 * IQR
     ```
   - Detected invalid extreme quantities (`quantity = 999`) representing only 0.19% of data and removed them to prevent statistical skewness.

---

## Key Insights & Exploratory Data Analysis
- **Demographics:** Customer age distribution spans primarily between 25 and 45 years.
- **Order Quantities:** Typical purchasing behavior lies within 1–10 items per order after stripping bulk test data.
- **Profit & Margins:** Checked price-to-profit scaling across categories including Electronics, Beauty, Groceries, and Furniture.

---

## Repository Structure
```text
├── 01_sales_retail_data_cleaning.ipynb   # Google Colab notebook with data cleaning code
├── 02_sales_retail_eda.py                # Standalone Python script with visualisation
├── 03_sales_retail_hypothesis_testing    # Python script with hypothesis testing
├── 04_sales_retail_rfm_clustering        # RFM Customer segmentation
├── README.md                     # Project documentation & summary
