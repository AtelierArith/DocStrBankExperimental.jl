```
svd_compact(A; kwargs...) -> U, S, Vᴴ
svd_compact(A, alg::AbstractAlgorithm) -> U, S, Vᴴ
svd_compact!(A, [USVᴴ]; kwargs...) -> U, S, Vᴴ
svd_compact!(A, [USVᴴ], alg::AbstractAlgorithm) -> U, S, Vᴴ
```

Compute the compact singular value decomposition (SVD) of the rectangular matrix `A` of size `(m, n)`, such that `A = U * S * Vᴴ`. Here, `U` is an isometric matrix (orthonormal columns) of size `(m, k)`, whereas  `Vᴴ` is a matrix of size `(k, n)` with orthonormal rows and `S` is a square diagonal matrix of size `(k, k)`, with `k = min(m, n)`.

!!! note
    The bang method `svd_compact!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `USVᴴ` as output.


See also [`svd_full(!)`](@ref svd_full), [`svd_vals(!)`](@ref svd_vals) and [`svd_trunc(!)`](@ref svd_trunc).
