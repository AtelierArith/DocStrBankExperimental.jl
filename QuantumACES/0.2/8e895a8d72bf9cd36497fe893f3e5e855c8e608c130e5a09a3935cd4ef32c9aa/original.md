```
sparse_covariance_inv(covariance_log::SparseMatrixCSC{Float64, Int}, mapping_lengths::Vector{Int}; epsilon::Real = 1e-12, warning::Bool = true)
```

Returns the inverse of the sparse block diagonal circuit log-eigenvalue estimator covariance matrix `covariance_log`, where the block sizes are specified by `mapping_lengths`, ensuring a smallest eigenvalue `epsilon` if the Cholesky factorisation fails, and warning if `warning` is `true`.
