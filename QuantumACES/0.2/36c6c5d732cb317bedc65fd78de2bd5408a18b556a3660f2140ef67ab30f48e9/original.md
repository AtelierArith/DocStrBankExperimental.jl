```
calc_ols_covariance(d::Design)
calc_ols_covariance(d::Design, covariance_log::SparseMatrixCSC{Float64, Int})
```

Returns the gate eigenvalue estimator covariance matrix for the ordinary least squares (OLS) estimator corresponding to the design `d` with circuit log-eigenvalue estimator covariance matrix `covariance_log`.
