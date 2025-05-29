```
calc_ls_covariance(d::Design; ls_type::Symbol = :gls, est_type::Symbol = :ordinary)
calc_ls_covariance(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; ls_type::Symbol = :gls, est_type::Symbol = :ordinary)
```

Returns the gate eigenvalue estimator covariance matrix for the least squares estimator specified by `ls_type` (`:gls`, `:wls`, or `:ols`) corresponding to the design `d` with circuit log-eigenvalue estimator covariance matrix `covariance_log`, with estimator type `est_type` (`:ordinary`, `:marginal`, or `:relative`).
