```
theilsen(setting, m, nsamples = 5000)
```

Theil-Sen estimator for multiple regression. 

# Arguments

  * `setting::RegressionSetting`: RegressionSetting object with a formula and dataset.
  * `m::Int`: Number of observations to be used in each iteration. This number must be in the range [p, n], where p is the number of regressors and n is the number of observations.
  * `nsamples::Int`: Number of m-samples. Default is 5000.

# Description

The function starts with a regression formula and datasets. The number of observations to be used in each iteration  is specified by the user. The function then randomly selects m observations from the dataset and performs an ordinary  least squares estimation. The estimated coefficients are saved. The process is repeated until nsamples regressions are estimated.  The multivariate median of the estimated coefficients is then calculated. In this case, the multivariate median is the point that minimizes the sum of distances to all the estimated coefficients. Hooke & Jeeves algorithm is used for the  optimization problem. 

# References

Dang, X., Peng, H., Wang, X., & Zhang, H. (2008). Theil-sen estimators in a multiple linear regression model.  Olemiss Edu.
