# US Cancer Incidence — Regression Modeling & Data Discovery

Two linked studies over the same county-level cancer dataset: a **statistical regression analysis** modeling what drives incidence and death rates, and a **Tableau discovery project** turning those findings into regional benchmarks for a health system.

**MGIS 650 — Introduction to Data Analytics and Business Intelligence** · Rochester Institute of Technology · Spring 2023
**Team of 4:** Akash Taploo · Raj Jasani · Sameer Bhattarai · Sneha Mondal

---

## Part 1 — Regression study

**Client framing:** American Cancer Society. **Question:** which factors actually move cancer incidence and death rates across US counties?

Built over roughly **30,000 county observations** joining cancer surveillance data with US Census socio-economic measures.

**Method, in order:**

1. Descriptive statistics and central-tendency comparison of incidence rate by state
2. Hypothesis tests on `recentTrend` (falling vs stable) and `studyCount`
3. ANOVA across four median-income bands
4. **Multicollinearity screening** — correlated predictors dropped on VIF score
5. **Residual diagnostics** — normal probability, versus-fits, histogram and versus-order plots to find outliers distorting the fit
6. Two multiple-regression models with categorical encoding for state and trend

**Results:**

| Model | R-sq (adj) | Significant predictors |
|---|---|---|
| Incidence rate | **53.37%** | median income, five-year trend, death rate, study count, state |
| Death rate | **63.39%** | incidence rate, five-year trend, median income, recent trend, study count, state |

**Findings worth stating plainly:**

- Kentucky (517.3), Delaware (498.2) and New York (497.5) carry the highest mean incidence; Arizona (369.3), New Mexico (370.9) and Utah (396.7) the lowest — the South highest as a region, the West lowest.
- Higher median income is associated with **lower** incidence, and the relationship is statistically significant.
- **Poverty estimate was *not* statistically significant** in either model, despite being an obvious candidate. Reporting a null result is part of the analysis, not a gap in it.

## Part 2 — Tableau data discovery

**Client framing:** Rochester Regional Health. **Question:** where should a regional health system target intervention?

**Regional factor comparison:**

| Factor | Highest | Lowest |
|---|---|---|
| Study count | West | South-East |
| Death rate | South-East | West |
| Poverty percent | South-East | North-East |
| Median income | North-East | South-East |

The South-East carries the worst death rate, the highest poverty and the lowest median income — while receiving the **fewest studies**. That inversion is the headline.

The analysis then narrows to New York: county-level heatmaps for incidence, death rate, median income, poverty percent and study count; a benchmark of New York against all other states; and the factors moving incidence in-state — closing with recommendations for RRH and health professionals.

## What's in this repo

| File | What it is |
|---|---|
| `cancer-incidence-regression-report.pdf` | 27-page regression study — method, diagnostics, model equations, appendix tables |
| `cancer-incidence-discovery.twbx` | Packaged Tableau workbook, 18 worksheets, data embedded (Tableau 2023.1) |
| `cancer-incidence-findings.pptx` | 20-slide deck written for a non-technical health-system audience |

## Data

County-level cancer surveillance data — incidence rate, death rate, average annual counts, five-year trend, recent trend, study count — joined with US Census measures for population, poverty estimate and median income.

## Notes

Academic coursework, completed spring 2023 as a four-person team project. Statistical modeling in **Minitab**; visualization in **Tableau**.

The workbook holds individual worksheets rather than assembled dashboards — the narrative lives in the deck, which pairs each view with its takeaway.
