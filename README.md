# 🎬 Netflix Dataset Analysis

A data analysis project exploring the **Netflix Movies and TV Shows dataset** usin&#x67;**&#xA0;Python, Pandas and Numpy.**

The project focuses on data cleaning, exploration, transformation, filtering, grouping, missing-value analysis, duplicate detection.

---

## 📌 Project Overview

This project analyzes a Netflix dataset containing information about movies and TV shows available on Netflix.

The analysis explores questions such as:

* How many Movies and TV Shows are in the dataset?
* Which countries have the most Netflix content?
* What are the most common ratings?
* How has Netflix content changed over the years?
* Which directors have missing information?
* What are the most common genres?
* How long are movies?
* How many titles were released after 2015?
* Which ratings contain incorrect duration values?
* Are there duplicate titles?
* What is the distribution of content by type and rating?

---

## 📂 Dataset

The dataset contains information about Netflix titles.

### Main Columns

| Column         | Description                         |
| -------------- | ----------------------------------- |
| `show_id`      | Unique ID of the title              |
| `type`         | Movie or TV Show                    |
| `title`        | Name of the title                   |
| `director`     | Director of the title               |
| `cast`         | Cast members                        |
| `country`      | Country of production               |
| `date_added`   | Date the title was added to Netflix |
| `release_year` | Original release year               |
| `rating`       | Content rating                      |
| `duration`     | Movie duration or number of seasons |
| `genres`       | Genres/categories of the title      |
| `description`  | Description of the title            |
| `age_years`    | Calculated age of the title         |

> **Note:** The original `listed_in` column was renamed to `genres`.

---

## 🛠️ Technologies Used

* 🐍 Python
* 🐼 Pandas
* Numpy
* ☁️ Google Colab / Jupyter Notebook
* 💻 GitHub

---

## 🧹 Data Cleaning

The project includes several data-cleaning operations:

### Missing Values

* Checked missing values in each column.
* Identified columns with the highest number of missing values.
* Checked missing and non-missing directors.
* Used appropriate methods to handle missing ratings.

### Rating Cleaning

Some values in the `rating` column were actually movie durations, such as:

```text
74 min
```

These incorrect rating values were identified and replaced with:

```text
UNRATED
```

### Date Cleaning

The `date_added` column was cleaned by:

* Removing extra spaces.
* Converting values to datetime.
* Extracting the year.
* Extracting the month.

New columns include:

```text
year_added
month_added
```

### Duration Cleaning

Movie duration information was extracted and converted into usable numerical data for analysis.

---

## 🔄 Data Transformation

Several transformations were performed during the analysis.

### Rename Column

```python
df.rename(columns={"listed_in": "genres"}, inplace=True)
```

### Create `age_years`

```python
df["age_years"] = 2026 - df["release_year"]
```

### Create Content Platform Column

```python
df["platform"] = "Netflix"
```

### Create Era Column

Titles were categorized into different eras based on their release year.

### Convert Data Type

The `release_year` column was converted to an integer data type where appropriate.

---

## 🔎 Exploratory Data Analysis

The project uses Pandas operations such as:

```python
df.shape
df.columns
df.info()
df.describe()
df.describe(include="object")
df.head()
df.tail()
```

Other operations include:

```python
value_counts()
unique()
nunique()
isnull()
notnull()
duplicated()
drop_duplicates()
```

---

## 🔍 Filtering

Examples of filtering performed in the project include:

### Movies Released After 2015

```python
df[(df["type"] == "Movie") & (df["release_year"] > 2015)]
```

### Titles From India

```python
df[df["country"].str.contains("India", na=False)]
```

### Using Multiple Conditions

```python
df[
    (df["type"] == "Movie") &
    (df["release_year"] > 2015)
]
```

---

## 📊 GroupBy Analysis

The project uses `groupby()` to analyze Netflix content from different perspectives.

Examples include:

### Titles by Country

```python
df.groupby("country")["title"].count()
```

### Content by Rating

```python
df.groupby("rating")["title"].count()
```

### Minimum and Maximum Release Year

```python
df.groupby("type")["release_year"].agg(["min", "max"])
```

### Content by Year

```python
df.groupby("release_year")["title"].count()
```

---

## 📅 Date Analysis

The `date_added` column was processed to analyze when content was added to Netflix.

Example:

```python
df["date_added"] = df["date_added"].str.strip()
df["date_added"] = pd.to_datetime(df["date_added"])
```

Then:

```python
df["year_added"] = df["date_added"].dt.year
df["month_added"] = df["date_added"].dt.month
```

---

## 📊 Analysis Topics

The workbook/notebook covers:

* Dataset dimensions
* Column information
* Data types
* Missing-value analysis
* Unique values
* Duplicate titles
* Movies vs TV Shows
* Country analysis
* Rating analysis
* Genre analysis
* Release-year analysis
* Date-added analysis
* Movie duration analysis
* Director analysis
* Title-length analysis
* Content age analysis
* GroupBy analysis
* Multi-condition filtering
* Sorting
* Aggregation

---

## 📁 Project Structure

```text
Netflix-Dataset-Analysis/
│
├── Netflix_dataset_analysis.ipynb
├── netflix_titles.csv
├── README.md
```

---

## 🚀 How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/Netflix-Dataset-Analysis.git
```

### 2. Open the Project

Open the project folder in:

* Jupyter Notebook
* Google Colab
* VS Code

### 3. Install Required Libraries

```bash
pip install pandas numpy
```

### 4. Load the Dataset

```python
import pandas as pd

df = pd.read_csv("netflix_titles.csv")
```

### 5. Start the Analysis

Run the notebook cells sequentially to reproduce the analysis.

---

## 🎯 Learning Objectives

This project was created to practice and demonstrate:

* Data loading
* Data cleaning
* Data preprocessing
* Pandas DataFrame operations
* Conditional filtering
* Missing-value handling
* Duplicate handling
* String operations
* Date/time operations
* GroupBy and aggregation
* Data transformation
* Exploratory Data Analysis (EDA)

---

## 💡 Key Pandas Concepts Practiced

```text
.head()
.tail()
.shape
.columns
.info()
.describe()
.loc[]
.iloc[]
.value_counts()
.unique()
.nunique()
.isnull()
.notnull()
.duplicated()
.drop_duplicates()
.sort_values()
.groupby()
.agg()
.str.contains()
.str.strip()
.to_datetime()
```

---

## 📌 Project Status

**Status:** Completed / Learning Project

This project is primarily focused on practicing **Exploratory Data Analysis and Pandas** using a real-world dataset.

---

## 👨‍💻 Author

**Yubaraj Shrestha**

GitHub: `https://github.com/shresthayuvi07-glitch`

---

## ⭐ If You Find This Project Useful

Feel free to **star ⭐ the repository** and explore the analysis.
