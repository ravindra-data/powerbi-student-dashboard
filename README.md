# 📊 Student Performance Dashboard — Power BI Project

An interactive Power BI dashboard for tracking student academic performance, attendance, and behaviour — built with a Star Schema data model, 11 DAX measures, and two report pages covering summary KPIs and individual student drill-through profiles.

---

## 📌 Project Overview

| Property | Details |
|---|---|
| Tool | Microsoft Power BI Desktop |
| File | Student_Performance_Dashboard.pbix |
| Student | Ravindra Kumar |
| GR ID | 11638 |
| Total Tables | 5 (3 Fact + 1 Dimension + 1 Measures) |
| Schema Type | Star Schema |
| Report Pages | 2 (Dashboard, Student Profile) |
| Total Visuals | 12 charts/tables/cards + 4 slicers + shapes & buttons |
| DAX Measures | 11 |

---

## 🗃️ Data Model — Tables

| Table | Type | Key Column | Role in Model |
|---|---|---|---|
| Students | Dimension Table | StudentID | Central dimension — Name, Class, Section |
| Scores | Fact Table | — | Academic records — Subject, Term, Score |
| Attendance | Fact Table | — | Attendance records — Date, Status, Reason |
| Behavior | Fact Table | — | Behaviour log — Date, BehaviorType, Notes |
| Measures (2) | Measures Table | — | All DAX calculated measures (no data rows) |

---

## 📋 Dataset Details

### 👤 Students (Dimension Table)
| Column | Description |
|---|---|
| Name | Student full name |
| Class | Student's class |
| Section | Student's section |

### 📝 Scores (Fact Table)
| Column | Description |
|---|---|
| Subject | Subject name |
| Term | Term (e.g. Term 1, Term 2) |
| Score | Marks obtained |

### ✅ Attendance (Fact Table)
| Column | Description |
|---|---|
| Date | Date of attendance record |
| Status | Present / Absent / Late |
| Reason | Reason for absence (if applicable) |

### 🧾 Behavior (Fact Table)
| Column | Description |
|---|---|
| Date | Date of behaviour incident |
| BehaviorType | Type/category of behaviour |
| Notes | Additional notes or remarks |

---

## 🔗 Relationships & Cardinality

| From Table (Dimension) | To Table (Fact) | Cardinality | Cross-Filter | Status |
|---|---|---|---|---|
| Students | Scores | 1 : * | Single | ✅ Active |
| Students | Attendance | 1 : * | Single | ✅ Active |
| Students | Behavior | 1 : * | Single | ✅ Active |

> **Schema:** Students sits at the centre as the core dimension table, with Scores, Attendance and Behavior as fact tables around it — a classic Star Schema design.

---

## 📐 DAX Measures (Measures (2) Table)

| Measure | Purpose |
|---|---|
| Total Students | Distinct count of all students |
| % Score | Average / aggregated score percentage |
| Average Score per Subject | Average score broken down by Subject |
| Attendance % | Present days as a percentage of total recorded days |
| Behavior Incidents | Total count of behaviour log entries |
| Behavior Count per Type | Count of behaviour entries grouped by BehaviorType |
| Subjects Count | Distinct count of subjects per student |
| Performance | Score/label used in the Top Students table |
| Performance Category | Categorical rating (e.g. Excellent / Good / Needs Improvement) |
| Student Class | Selected student's class — shown on the Profile card |
| Student Section | Selected student's section — shown on the Profile card |

---

## 📊 Report Pages & Visuals

### Page 1 — Dashboard

| Visual | Type | Fields Used |
|---|---|---|
| Score Trend by Term | Line Chart | Term (axis), % Score (value) |
| Average Score per Subject | Clustered Column Chart | Subject (axis), Average Score per Subject (value) |
| Behaviour by Type | Donut Chart | BehaviorType (legend), Behavior Count per Type (value) |
| Top Students | Table | Name, Subject, % Score, Attendance %, Performance |
| KPI Cards (×3) | Card | Total Students · Attendance % · Average Score per Subject |
| Slicers (×4) | Slicer | Class · Section · Subject · Term |
| Text Boxes (×2) | Text Box | Titles / labels |

### Page 2 — Student Profile *(Drill-through page)*

| Visual | Type | Fields Used |
|---|---|---|
| Student Header Card | Card Group | Name, Performance Category, Student Class, Student Section |
| Score Card | Card | % Score |
| Attendance Card | Card | Attendance % |
| Behaviour Card | Card | Behavior Incidents |
| Subjects Card | Card | Subjects Count |
| Score by Subjects | Clustered Column Chart | Subject (axis), % Score (value) |
| Trend by Term | Line Chart | Term (axis), % Score (value) |
| Attendance Record | Table | Status, Reason, Date |
| Behaviour Log | Table | Date, BehaviorType, Notes |
| Back Button + Shapes | Action Button / Shape / Group | Navigation & layout elements |

> **Student Profile** functions as a drill-through detail page — select any student from the Dashboard table to open their full individual profile with score breakdown, attendance log and behaviour history.

---

## 🚧 Challenges & Solutions

| Challenge | Solution |
|---|---|
| Combining 4 different tables into one consistent model | Built one-to-many relationships from Students to each fact table using a common Student key |
| Showing both a summary view and a single-student detail view | Split into two pages — Dashboard (aggregate KPIs & trends) and Student Profile (drill-through detail) |
| Repeating calculations (averages, counts, %) across many visuals | Centralised all calculations as DAX measures in a dedicated Measures (2) table for reuse and easier maintenance |
| Letting users filter every visual consistently | Added 4 slicers on the Dashboard page (Class, Section, Subject, Term) driven by relationships from Students/Scores |

---

## 🛠️ Tech Stack

- **Tool:** Microsoft Power BI Desktop
- **Features Used:** Model View, Report View, Drill-through, Slicers, DAX Measures, Star Schema
- **Operations:** Data Modelling, Relationship Cardinality, DAX Calculations, KPI Cards, Drill-through Navigation

---

## 💡 What I Learned

- Designing a **Star Schema** with one central Dimension table and multiple Fact tables
- Writing **DAX Measures** for KPIs like % Score, Attendance %, Performance Category
- Building a **two-page interactive report** — a summary Dashboard and a drill-through Student Profile page
- Using **Slicers** to enable consistent cross-visual filtering by Class, Section, Subject and Term
- Creating **drill-through navigation** so users can jump from a summary table to an individual student's full profile
- Organising all calculated logic in a **dedicated Measures table** to keep the model clean

---

## 📁 Project Structure

```
student-performance-dashboard/
│
├── Student_Performance_Dashboard.pbix     # Main Power BI file
├── PowerBI_StudentDashboard_Summary.pdf   # Data model & report summary
├── datasets/
│   ├── Students.xlsx                      # Student dimension data
│   ├── Scores.xlsx                        # Academic scores fact data
│   ├── Attendance.xlsx                    # Attendance fact data
│   └── Behavior.xlsx                      # Behaviour fact data
├── screenshots/
│   └── dashboard.png                      # Dashboard preview
└── README.md                              # Project documentation
```

---
*Submitted by: Ravindra Kumar | GR ID: 11638*
