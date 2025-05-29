```
lq_null(A; kwargs...) -> Nᴴ
lq_null(A, alg::AbstractAlgorithm) -> Nᴴ
lq_null!(A, [Nᴴ]; kwargs...) -> Nᴴ
lq_null!(A, [Nᴴ], alg::AbstractAlgorithm) -> Nᴴ
```

For a (m, n) matrix A, compute the matrix `Nᴴ` corresponding the final `n - min(m, n)` rows  oft the unitary `Q` factor in the full LQ decomposition of `A`, i.e. the rows that are not present in the `Q` factor of the compact LQ decomposition. The matrix `Nᴴ` is such that the isometric matrix `N = adjoint(Nᴴ)` contains an orthonormal basis for the kernel (null space) of `A` as its columns, i.e. `A * N = 0` or thus `A * adjoint(Nᴴ) = 0`.

!!! note
    The bang method `lq_null!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `Nᴴ` argument as output.


!!! note
    The matrix `Nᴴ` is empty when `m >= n`.


See also [`qr_full(!)`](@ref lq_full) and [`qr_compact(!)`](@ref lq_compact).
