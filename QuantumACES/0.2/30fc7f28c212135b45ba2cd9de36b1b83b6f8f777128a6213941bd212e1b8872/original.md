```
calc_ols_moments(d::Design; est_type::Symbol = :ordinary)
calc_ols_moments(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; est_type::Symbol = :ordinary)
```

Returns the expectation and variance of the normalised RMS error for the ordinary least squares (OLS) estimator corresponding to the design `d` with circuit log-eigenvalue estimator covariance matrix `covariance_log`, with estimator type `est_type` (`:ordinary`, `:marginal`, or `:relative`).
