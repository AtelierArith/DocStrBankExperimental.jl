```
calc_covariance_log(covariance::SparseMatrixCSC{Float64, Int}, eigenvalues::Vector{Float64})
calc_covariance_log(d::Design; warning::Bool = true)
```

Returns the covariance matrix of the circuit log-eigenvalues corresponding to the circuit eigenvalues `eigenvalues` with covariance matrix `covariance`, using values generated from the design `d` and, if `warning` is `true`, warns that if `d.full_covariance` is `false` then this will only generate the diagonal of the covariance matrix.
