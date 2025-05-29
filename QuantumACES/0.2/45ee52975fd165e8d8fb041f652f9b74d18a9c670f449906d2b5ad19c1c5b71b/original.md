```
calc_precision_matrix(design_matrix::SparseMatrixCSC{Float64, Int}, gate_eigenvalues::Vector{Float64}, covariance_log_inv::SparseMatrixCSC{Float64, Int})
calc_precision_matrix(d::Design, gate_eigenvalues::Vector{Float64}; diagonal::Bool = false)
calc_precision_matrix(d::Design; diagonal::Bool = false)
```

Returns the precision matrix, namely the inverse of the generalised least squares gate eigenvalue estimator covariance matrix, corresponding to the design `d` with design matrix `design_matrix`, gate eigenvalues `gate_eigenvalues` and circuit log-eigenvalue estimator covariance matrix inverse `covariance_log_inv`. Ordinarily this yields the precision matrix for generalise least squares, but if `diagonal` is `true` it calculates the inverse of the diagonal of the covariance matrix, rather than the inverse of the full matrix, yielding the precision matrix for both generalised and weighted least squares if the circuit eigenvalue estimators were uncorrelated.
