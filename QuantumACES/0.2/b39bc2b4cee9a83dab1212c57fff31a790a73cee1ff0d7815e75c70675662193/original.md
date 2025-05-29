```
calc_ls_moments(d::Design; ls_type::Symbol = :gls, est_type::Symbol = :ordinary, est_weight::Float64 = 0.5)
calc_ls_moments(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; ls_type::Symbol = :gls, est_type::Symbol = :ordinary, est_weight::Float64 = 0.5)
```

Returns the expectation and variance of the normalised RMS error for the least squares estimator specified by `ls_type` (`:gls`, `:wls`, or `:ols`) corresponding to the design `d` with circuit log-eigenvalue estimator covariance matrix `covariance_log`, with estimator type `est_type` (`:ordinary`, `:marginal`, or `:relative`). If `est_type` is instead set to `:sum` or `:prod`, computes the arithmetic or geometric mean of the ordinary and relative precision moments, weighted by `est_weight`, the weighting allocated to the ordinary precision moments.
