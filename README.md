# Messy Employee Dataset Cleaning

## About

This project focuses on cleaning a messy employee dataset using Python and Pandas. The goal was to identify data quality issues, handle missing values, correct data types, and prepare the dataset for further analysis.

## Cleaning Process

### 1. Data Inspection
- Inspected the dataset using `head()`, `info()`, and `describe()`.
- Checked missing values and duplicate rows.
- Inspected categorical values and checked for extra whitespace.

### 2. Handling Data Types
- Loaded the `Phone` column as a string using the `dtype` argument in `pd.read_csv()`. Phone numbers are identifiers, not numerical values, so they should not be treated as numbers.
- Converted `Join_Date` into a datetime format using `pd.to_datetime()` with `errors="coerce"`.

### 3. Cleaning Phone Numbers
- Found that all phone numbers contained a leading negative sign.
- Removed the negative sign from the phone numbers while keeping the column as a string.
- Checked phone number lengths and found that some numbers contained fewer than 10 digits. These were left unchanged because the missing digits could not be reliably reconstructed.

### 4. Handling Missing Values

| Column | Missing Values | Action Taken | Reason |
|---|---:|---|---|
| `Age` | 211 | Filled with median (30) | The median was used to fill missing ages without removing rows and is less affected by extreme values. |
| `Salary` | 24 | Filled with median (~85,547.87) | The median provides a reasonable replacement for missing salaries without being heavily influenced by extreme values. |

### 5. Checking Categorical Values
- Checked categorical columns for leading and trailing whitespace.
- No extra whitespace was found.
- Existing categorical values were kept unchanged.

### 6. Final Validation
- Checked for missing values across all columns.
- Verified data types.
- Checked for duplicate rows.
- Reviewed the numerical ranges of `Age` and `Salary`.

## Final Results

| Check | Result |
|---|---|
| Total Rows | 1,020 |
| Total Columns | 12 |
| Duplicate Rows | 0 |
| Missing Values | 0 |
| Phone Data Type | String |
| Join_Date Data Type | Datetime |

The dataset was cleaned and exported as `cleaned_employee.csv`.

## How to Run

1. Clone this repository.
2. Install [uv](https://docs.astral.sh/uv/), if you haven't already.
3. Navigate to the project directory:

   ```bash
   cd messy-employee-dataset
   ```

4. Create a virtual environment and install dependencies:

   ```bash
   uv sync
   ```

5. Open the notebook and run the cells from beginning to end.

The cleaned dataset will be saved inside the `data` folder.

## Project Reference

[Clean CSV – roadmap.sh](https://roadmap.sh/projects/clean-csv)
