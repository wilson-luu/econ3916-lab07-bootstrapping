# Estimation & Bootstrapping — Quantifying Uncertainty Without a Formula

**Objective:** This project demonstrates how to quantify the precision of statistical estimates by constructing sampling distributions, transitioning from theoretical parametric formulas (like the Central Limit Theorem) to simulation-based non-parametric bootstrapping for statistics that lack closed-form standard errors.

**Methodology:**
* Loaded the UCI Adult Census Income data (32,561 respondents).
* Separated the standard deviation of the data from the standard error of an estimate, and checked the s/sqrt(n) relationship across four sample sizes.
* Built parametric confidence intervals from the CLT and showed the CLT converges quickly for age and slowly for capital gains.
* Ran the bootstrap by hand, then with scipy.stats.bootstrap.
* Found a degenerate case: the bootstrap SE of the median of 32,561 whole-number ages is exactly 0.0000. Every resample returns the same median, because with that many ties the median is pinned. The bootstrap is reporting a real property of the data, not failing.
* Compared percentile and BCa intervals on a heavily skewed variable.
* Bootstrapped a two-sample difference in mean weekly hours.
* Asked an AI to write a bootstrap-interval function, revised my prompt once, and checked the function against my own intervals.
* Ran a coverage simulation on lognormal data at n=50. 

**Key Findings:**
For the MEAN, the nominal 95% parametric interval covered 92.5% and the percentile bootstrap 91.5%, a gap inside the Monte Carlo standard error of about 1.3 points, so the two methods are indistinguishable here and both under-cover slightly. For the MEDIAN, the mean-centred parametric interval covered only about 66.8% while the bootstrap held near its nominal level. The bootstrap effectively quantifies uncertainty for statistics lacking formulas, but it does not inherently cure skewness faster than the CLT when parametric equations exist.
