```
deepestregression(setting; maxit = 1000)
```

Estimate Deepest Regression paramaters.

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `maxit`: Maximum number of iterations

# Description

Estimates Deepest Regression Estimator coefficients.

# References

Van Aelst S., Rousseeuw P.J., Hubert M., Struyf A. (2002). The deepest regression method. Journal of Multivariate Analysis, 81, 138-166.

# Output

  * `betas`: Vector of regression coefficients estimated.
