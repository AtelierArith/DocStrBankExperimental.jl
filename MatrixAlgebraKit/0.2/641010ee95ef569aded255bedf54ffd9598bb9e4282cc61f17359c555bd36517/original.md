```
svd_full(A; kwargs...) -> U, S, Vᴴ
svd_full(A, alg::AbstractAlgorithm) -> U, S, Vᴴ
svd_full!(A, [USVᴴ]; kwargs...) -> U, S, Vᴴ
svd_full!(A, [USVᴴ], alg::AbstractAlgorithm) -> U, S, Vᴴ
```

Compute the full singular value decomposition (SVD) of the rectangular matrix `A` of size `(m, n)`, such that `A = U * S * Vᴴ`. Here, `U` and `Vᴴ` are unitary matrices of size `(m, m)` and `(n, n)` respectively, and `S` is a diagonal matrix of size `(m, n)`.

!!! note
    The bang method `svd_full!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `USVᴴ` as output.


See also [`svd_compact(!)`](@ref svd_compact), [`svd_vals(!)`](@ref svd_vals) and [`svd_trunc(!)`](@ref svd_trunc).
