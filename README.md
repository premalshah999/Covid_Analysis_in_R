# COVID-19 Policy Timing Optimization

[![R](https://img.shields.io/badge/R-4.0+-blue.svg)](https://www.r-project.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![RMarkdown](https://img.shields.io/badge/RMarkdown-Ready-orange.svg)](https://rmarkdown.rstudio.com/)

> **When should governments act to prevent healthcare system collapse?**  
> A data-driven analysis of COVID-19 policy timing using machine learning.

![Policy Analysis](Policy_Timing_Optimization_files/figure-html/timing_visualization-1.png)

## 📋 Overview

This project analyzes **85,000+ observation-days** across **198 regions worldwide** to determine the optimal timing for government policy interventions during the COVID-19 pandemic. Using the [COVID-19 Data Hub](https://covid19datahub.io/), I built predictive models that can forecast ICU surges **14 days in advance** with exceptional accuracy.

### Key Findings

| Finding | Detail |
|---------|--------|
| 🎯 **Prediction Accuracy** | Random Forest achieves **AUC 0.94** for surge prediction |
| ⏰ **Warning Window** | Governments have **16 days** to act when ICU hits 10-15 per 100k |
| 📊 **Best Predictor** | Current ICU utilization is the strongest predictor of future crises |
| 🛡️ **Policy Effect** | High-stringency policies associated with **~3% lower** surge rates |

## 🚀 Quick Start

### Prerequisites

- [R](https://www.r-project.org/) (version 4.0 or higher)
- [RStudio](https://posit.co/download/rstudio-desktop/) (recommended)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/premalshah999/Covid_Analysis_in_R.git
   cd Covid_Analysis_in_R
   ```

2. **Install required packages**
   ```r
   # Run in R console
   required_packages <- c(
     "COVID19", "tidyverse", "lubridate", "zoo", "caret", 
     "randomForest", "pROC", "ggplot2", "gridExtra", "scales",
     "knitr", "kableExtra", "plotly", "viridis", "boot"
   )
   
   install.packages(required_packages)
   ```

3. **Run the analysis**
   ```r
   # Open in RStudio and knit, or run:
   rmarkdown::render("Policy_Timing_Optimization.Rmd")
   ```

## 📊 Project Structure

```
├── Policy_Timing_Optimization.Rmd    # Main analysis (R Markdown)
├── Policy_Timing_Optimization.html   # Rendered HTML report
├── Policy_Timing_Optimization.pdf    # PDF version
├── Policy_Timing_Optimization_files/ # Generated figures
│   ├── figure-html/                  # PNG visualizations
│   └── figure-latex/                 # PDF visualizations
├── Policy_Timing_Optimization_cache/ # Cached model results
├── TROUBLESHOOTING_GUIDE.md          # Common issues & solutions
└── README.md                         # This file
```

## 🔬 Methodology

### Data Source
- **COVID-19 Data Hub**: Comprehensive database from University of Milan aggregating official pandemic statistics
- **Oxford Government Response Tracker**: Policy stringency index (0-100 scale)
- **Coverage**: 2020-2024, 198 regions with robust healthcare tracking

### Data Processing Pipeline
1. **Region Selection**: Filter to regions with ≥30% ICU data availability
2. **Negative Value Correction**: Handle reporting corrections
3. **Outlier Detection**: Flag values >10× regional median
4. **Missing Value Imputation**: Forward-fill for gaps ≤7 days
5. **Smoothing**: 7-day rolling averages to remove weekly artifacts

### Models Implemented

| Model | Purpose | Performance |
|-------|---------|-------------|
| **Logistic Regression** | Interpretable baseline | AUC: 0.69 |
| **Random Forest** | High-accuracy prediction | AUC: 0.94 |

### Validation Approach
- Region-based train/test split (prevents data leakage)
- Bootstrap confidence intervals
- Sensitivity analysis across thresholds

## 📈 Visualizations

The analysis includes 10+ professional visualizations:

- **ICU Surge Patterns**: Geographic and temporal variation
- **Policy Stringency Evolution**: How governments responded over time
- **Model Comparison**: ROC curves and performance metrics
- **Feature Importance**: What drives predictions
- **Bootstrap Results**: Uncertainty quantification

## 🎯 Key Results

### ICU Surge Prediction
```
Random Forest Performance:
- AUC: 0.94 (Excellent)
- Sensitivity: 85%+
- Specificity: 90%+
- Lead Time: 14 days
```

### Policy Effectiveness
- **High stringency (≥60)**: 22.2% surge rate
- **Low stringency (<40)**: 25.6% surge rate
- **Difference**: Modest but consistent protective effect

### Decision Framework
| ICU Level (per 100k) | Risk Level | Recommended Action |
|---------------------|------------|-------------------|
| < 5 | 🟢 Safe | Monitor weekly |
| 5-10 | 🟡 Elevated | Increase vigilance |
| 10-15 | 🟠 High Risk | Prepare interventions |
| ≥ 15 | 🔴 Crisis | Immediate action required |

## ⚠️ Limitations

- **Geographic Bias**: Predominantly Western European and North American data
- **Observational Study**: Associations, not causal claims
- **Confounding Factors**: Economic conditions, cultural compliance, healthcare capacity
- **Temporal Dynamics**: Virus variants evolved over study period

## �️ Troubleshooting

Common issues and solutions are documented in [TROUBLESHOOTING_GUIDE.md](TROUBLESHOOTING_GUIDE.md).

**Quick fixes:**
- **"2 factor levels" error**: Change `set.seed(42)` to `set.seed(123)`
- **Memory issues**: Reduce `ntree = 500` to `ntree = 250`
- **Slow knitting**: Enable caching in chunk options

## 📚 References

1. Guidotti, E., & Ardia, D. (2020). COVID-19 Data Hub. *Journal of Open Source Software*, 5(51), 2376.
2. Hale, T., et al. (2021). A global panel database of pandemic policies (Oxford COVID-19 Government Response Tracker). *Nature Human Behaviour*, 5, 529-538.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Premal Shah**
- GitHub: [@premalshah999](https://github.com/premalshah999)

## 🙏 Acknowledgments

- [COVID-19 Data Hub](https://covid19datahub.io/) for comprehensive pandemic data
- [Oxford Government Response Tracker](https://www.bsg.ox.ac.uk/research/covid-19-government-response-tracker) for policy stringency metrics
- R community for excellent open-source packages

---

⭐ **If you find this analysis useful, please consider giving it a star!**
