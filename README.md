# 🛫 TSA Claims Data Analysis (2002–2017)

## 📌 Overview

This project focuses on **data cleaning, preprocessing, and analysis** of TSA (Transportation Security Administration) claims data from 2002 to 2017 using **SAS**.

The goal is to transform raw, inconsistent data into a clean and structured dataset, then generate **insightful statistical reports and visualizations** to support decision-making.

---

## 🎯 Objectives

* Import raw CSV data into SAS
* Perform **data cleaning and preprocessing**
* Handle:

  * Missing values
  * Inconsistent text formats
  * Invalid date records
* Create **analysis-ready dataset**
* Generate **PDF report** with:

  * Statistical summaries
  * Frequency distributions
  * Visual charts

---

## 📂 Project Structure

```
📁 Project/
│── TSAClaims2002_2017.csv     # Raw dataset
│── README.md                  # Project documentation
│── TSA_Claims_Report.pdf      # Final generated report
```

---

## ⚙️ Data Processing Pipeline

### 1️⃣ Data Import

* Load CSV file using `PROC IMPORT`
* Automatically detect variable types

---

### 2️⃣ Data Inspection

* `PROC CONTENTS` → structure of dataset
* `PROC PRINT` → preview sample records

---

### 3️⃣ Remove Duplicates

* Remove fully duplicated rows using:

```
PROC SORT NODUPRECS
```

---

### 4️⃣ Data Cleaning

#### ✔ Text Standardization

* Convert to uppercase → `UPCASE()`
* Normalize format → `PROPCASE()`
* Remove extra spaces → `STRIP()`

#### ✔ Missing Handling

Replace:

```
Missing or '-' → "Unknown"
```

#### ✔ Fix Inconsistent Values

Examples:

* `"Deny"` → `"Denied"`
* `"Settle"` → `"Settled"`
* `"Closed:canceled"` → `"Closed: Canceled"`

---

### 5️⃣ Date Validation

Records are flagged as:

```
Date_Issues = "Needs Review"
```

If:

* Missing dates
* Dates Out of the range (2002–2017)
* Incident_Date > Date_Received

---

### 6️⃣ Final Clean Dataset

* Drop unnecessary columns:

```
County, City
```

* Apply formats:

```
Close_Amount → Currency
Dates → DATE9 format
```

---

### 7️⃣ Analysis Dataset

Filter only valid records:

```
Date_Issues ≠ "Needs Review"
```

Add:

```
Incident_Year = YEAR(Incident_Date)
```

---

### 8️⃣ State-Level Analysis

Dynamic filtering using:

```
%let selected_state = CALIFORNIA;
```

---

## 📊 Analysis Performed

### 🔹 Overall Analysis

* Date Issues distribution
* Number of claims per year
* Bar chart (Incident Year vs Claims)

---

### 🔹 State-Level Analysis

For selected state:

* Claim Type distribution
* Claim Site distribution
* Disposition analysis
* Close Amount statistics:

  * Mean
  * Min
  * Max
  * Sum

---

## 📈 Visualization

Generated using:

```
PROC SGPLOT
```

Example:

* Bar Chart for yearly claims

---

## 📄 Output

📌 Final Report:

```
TSA_Claims_Report.pdf
```

Contains:

* Cleaned data insights
* Statistical summaries
* Visualizations

---

## 🧠 Key Insights (Example)

* Data cleaning significantly improves analysis accuracy
* Many inconsistencies exist in raw categorical data
* Date validation is critical for time-based analysis
* Claims distribution varies across years and locations

---

## 🚀 Future Improvements

* Add **interactive dashboards (Power BI / Tableau)**
* Perform **predictive analysis**
* Detect anomalies in claims
* Integrate machine learning models

---

## 🛠️ Technologies Used

* **SAS**

  * PROC IMPORT
  * PROC SORT
  * DATA Step
  * PROC FREQ
  * PROC MEANS
  * PROC SGPLOT
  * ODS PDF

---

## 👨‍💻 Author

**Obaidah Essam**
AI & Data Science Student
EJUST – Egypt-Japan University of Science and Technology

---

## ⭐ Notes

This project demonstrates:

* Strong data preprocessing skills
* Structured analytical workflow
* Professional reporting using SAS

---

## 📬 Contact

If you have any questions or suggestions, feel free to reach out!

---
