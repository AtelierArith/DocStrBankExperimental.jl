```
qr_null(A; kwargs...) -> N
qr_null(A, alg::AbstractAlgorithm) -> N
qr_null!(A, [N]; kwargs...) -> N
qr_null!(A, [N], alg::AbstractAlgorithm) -> N
```

For a (m, n) matrix A, compute the matrix `N` corresponding the final `m - min(m, n)` columns  of the unitary `Q` factor in the full QR decomposition of `A`, i.e. the columns that are not present in the `Q` factor of the compact QR decomposition. The isometric matrix `N` contains an orthonormal basis for the cokernel of `A` as its columns, i.e. `adjoint(A) * N = 0`.

!!! note
    The bang method `qr_null!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `N` argument as output.


!!! note
    The matrix `N` is empty when `m <= n`.


See also [`lq_full(!)`](@ref lq_full) and [`lq_compact(!)`](@ref lq_compact).
