```
calc_gate_probabilities_covariance(d::Design; ls_type::Symbol = :gls, est_type::Symbol = :ordinary, unpad::Bool = false)
calc_gate_probabilities_covariance(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; ls_type::Symbol = :gls, est_type::Symbol = :ordinary, unpad::Bool = false)
```

Returns the padded gate error probabilities estimator covariance matrix for the least squares estimator specified by `ls_type` (`:gls`, `:wls`, or `:ols`) corresponding to the design `d` with circuit log-eigenvalue estimator covariance matrix `covariance_log`, with estimator type `est_type` (`:ordinary`, `:marginal`, or `:relative`). Instead returns the unpadded gate error probabilities estimator covariance matrix if `unpad` is `true`, which is stripped of the covariance with the identity error probabilities.
