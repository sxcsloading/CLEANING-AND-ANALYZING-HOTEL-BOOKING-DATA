# Group 06 — Hotel Booking Data Practice Exercise

## 1. Members and assignments

| Name | Student ID | Role |Responsibillity | Explicable portion |
|---|---|---|---|---|
|Phạm Ngọc Mai | 11255166 | Data Engineer | EDA, Data Cleaning, Output Standardization, Code QA| Handled the data preparation phase. Ensured the raw data was properly cleaned, standardized, and that all scripts ran correctly without errors.|
|Nguyễn Hà Phương | 11256961| Data Analyst | Visualization, Analysis, Insight Generation, Reporting (Word & PPT) | Analyzed the cleaned dataset to find key trends. Created all visual charts and was responsible for putting together the final Word report and PowerPoint slides.|


## 2. How to re-run

1. Extract `NhomXX_KhachSan.zip`, preserving the directory structure.
2. Open `hotel_analysis.ipynb` in the root directory; select **Restart & Run all**. 
(For Colab: upload the notebook, upload `data/hotel_bookings_dirty.csv` to the Files panel, then run all cells.)
3. Results are saved to the `outputs/` directory (5 data files, `tables/`, and `figures/`), along with `outputs/b8_merge_conflicts.csv` (a list of merge conflicts).

Total execution time on the team's machine: approximately 5 seconds.

## 3. Environment and libraries

| Component | Version |
|---|---|
| Python | 3.14.7 (verified on Colab, Python 3.12) |
| pandas | 2.3.3 (Colab: 2.2.x) |
| matplotlib | 3.11.2 |
| seaborn (if used) | Not used |
| Environment | Jupyter / Google Colab |

## 4. Data source

Antonio, N., de Almeida, A., & Nunes, L. (2019). Hotel booking demand datasets. *Data in Brief*, 22, 41–49. https://doi.org/10.1016/j.dib.2018.11.126 (CC BY 4.0).
Educational compilation `hotel_bookings_dirty.csv` (10,325 rows × 24 columns); data snapshot: 2017-09-14.

## 5. Team-specific rules (deviating from or supplementing the assignment)

| # | Scenario | Team's chosen rule | Rationale | Impact on results |
|---|---|---|---|---|
| 1 | Value conflict when merging identical `booking_id` | Select the non-missing value from the row with the smallest `row_id` | Simple, reproducible, no guesswork | 15 bookings had conflicts in `adr` (8) and `lead_time` (7); differences were minor; see `outputs/b8_merge_conflicts.csv` |
| 2 | Rows identical across all 23 columns | Drop immediately in Step 1 (keep the first row), record as `dropped` in `row_lineage` | Distinguish between "exact duplicates" and "duplicates with differences" (merged in B8) | 181 rows `dropped`, 144 rows `merged` |
| 3 | After merging B8 | Re-apply rule from Section 5.3 (recalculate `is_canceled` based on status) | `is_canceled` and status may originate from different rows | 0 rows requiring further correction |
| 4 | `UK` code in `country` | Map to `GBR` (despite the 2-letter format) | Mapping table in Section 5.1 | 25 raw rows |

## 6. List of submitted files

- [x] `hotel_analysis.ipynb`
- [x] `Bao_cao_Khach_san.docx` (in English, with `.pdf` version)
- [x] `data/hotel_bookings_dirty.csv`
- [x] `outputs/` — 5 data files
- [x] `outputs/tables/` — 14 tables
- [x] `outputs/figures/` — 8 figures

