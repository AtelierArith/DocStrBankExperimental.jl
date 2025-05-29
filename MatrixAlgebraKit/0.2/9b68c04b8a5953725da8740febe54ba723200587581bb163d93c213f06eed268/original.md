```
svd_trunc(A; kwargs...) -> U, S, Vᴴ
svd_trunc(A, alg::AbstractAlgorithm) -> U, S, Vᴴ
svd_trunc!(A, [USVᴴ]; kwargs...) -> U, S, Vᴴ
svd_trunc!(A, [USVᴴ], alg::AbstractAlgorithm) -> U, S, Vᴴ
```

Compute a partial or truncated singular value decomposition (SVD) of `A`, such that `A * (Vᴴ)' =  U * S`. Here, `U` is an isometric matrix (orthonormal columns) of size `(m, k)`, whereas  `Vᴴ` is a matrix of size `(k, n)` with orthonormal rows and `S` is a square diagonal matrix of size `(k, k)`, with `k` is set by the truncation strategy.

!!! note
    The bang method `svd_trunc!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `USVᴴ` as output.


See also [`svd_full(!)`](@ref svd_full), [`svd_compact(!)`](@ref svd_compact) and [`svd_vals(!)`](@ref svd_vals).
