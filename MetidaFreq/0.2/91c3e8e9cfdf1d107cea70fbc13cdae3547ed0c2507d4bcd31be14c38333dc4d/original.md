```
propci(x::Int, n::Int; level = 0.95, method = :default)
```

Proportion confidence interval.

`method`:

  * `:wilson` | `:default` - Wilson's confidence interval (CI) for a single proportion (wilson score) (Wilson, 1927);
  * `:wilsoncc` - Wilson's CI with continuity correction (CC);
  * `:cp` - Clopper-Pearson exact CI (Clopper&Pearson, 1934);
  * `:blaker` - Blaker exact CI for discrete distributions (Blaker, 2000);
  * `:soc` - SOC: Second-Order corrected CI;
  * `:arc` - Arcsine CI;
  * `:wald` - Wald CI without CC;
  * `:waldcc` - Wald CI with CC (1/2/n);
  * `:ac` - Agresti-Coull;
  * `:jeffrey` - Jeffreys interval (Brown et al,2001).

Reference:

  * Wilson, E.B. (1927) Probable inference, the law of succession, and statistical inference J. Amer.Stat. Assoc 22, 209–212;
  * Clopper, C. and Pearson, E.S. (1934) The use of confidence or fiducial limits illustrated in the caseof the binomial.Biometrika26, 404–413;
  * Agresti A. and Coull B.A. (1998) Approximate is better than "exact" for interval estimation of binomial proportions. American Statistician, 52, pp. 119-126.
  * Newcombe, R. G. (1998) Two-sided confidence intervals for the single proportion: comparison of seven methods, Statistics in Medicine, 17:857-872 https://pubmed.ncbi.nlm.nih.gov/16206245/
  * Blaker, H. (2000). Confidence curves and improved exact confidence intervals for discrete distributions, Canadian Journal of Statistics 28 (4), 783–798;
  * Pires, Ana & Amado, Conceição. (2008). Interval Estimators for a Binomial Proportion: Comparison of Twenty Methods. REVSTAT. 6. 10.57805/revstat.v6i2.63.
