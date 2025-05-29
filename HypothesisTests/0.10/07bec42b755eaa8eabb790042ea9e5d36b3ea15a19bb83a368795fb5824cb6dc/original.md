```
confint(test::PowerDivergenceTest; level = 0.95, tail = :both, method = :auto)
```

Compute a confidence interval with coverage `level` for multinomial proportions using one of the following methods. Possible values for `method` are:

  * `:auto` (default): If the minimum of the expected cell counts exceeds 100, Quesenberry-Hurst intervals are used, otherwise Sison-Glaz.
  * `:sison_glaz`: Sison-Glaz intervals
  * `:bootstrap`: Bootstrap intervals
  * `:quesenberry_hurst`: Quesenberry-Hurst intervals
  * `:gold`: Gold intervals (asymptotic simultaneous intervals)

# References

  * Agresti, Alan. Categorical Data Analysis, 3rd Edition. Wiley, 2013.
  * Sison, C.P and Glaz, J. Simultaneous confidence intervals and sample size determination for multinomial proportions. Journal of the American Statistical Association, 90:366-369, 1995.
  * Quesensberry, C.P. and Hurst, D.C. Large Sample Simultaneous Confidence Intervals for Multinational Proportions. Technometrics, 6:191-195, 1964.
  * Gold, R. Z. Tests Auxiliary to $χ^2$ Tests in a Markov Chain. Annals of Mathematical Statistics, 30:56-74, 1963.
