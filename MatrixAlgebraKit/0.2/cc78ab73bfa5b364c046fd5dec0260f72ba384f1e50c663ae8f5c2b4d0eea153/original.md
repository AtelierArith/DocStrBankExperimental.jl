```
svd_vals(A; kwargs...) -> S
svd_vals(A, alg::AbstractAlgorithm) -> S
svd_vals!(A, [S]; kwargs...) -> S
svd_vals!(A, [S], alg::AbstractAlgorithm) -> S
```

Compute the vector of singular values of `A`, such that for an M×N matrix `A`, `S` is a vector of size `K = min(M, N)`, the number of kept singular values.

See also [`svd_full(!)`](@ref svd_full), [`svd_compact(!)`](@ref svd_compact) and [`svd_trunc(!)`](@ref svd_trunc).
