```
calc_wls_covariance(d::Design)
calc_wls_covariance(d::Design, covariance_log::SparseMatrixCSC{Float64, Int})
```

Returns the gate eigenvalue estimator covariance matrix for the weighted least squares (WLS) estimator corresponding to the design `d` with circuit log-eigenvalue estimator covariance matrix `covariance_log`.
