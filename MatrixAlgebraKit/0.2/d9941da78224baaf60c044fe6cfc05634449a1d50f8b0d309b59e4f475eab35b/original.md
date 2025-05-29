```
lq_compact(A; kwargs...) -> L, Q
lq_compact(A, alg::AbstractAlgorithm) -> L, Q
lq_compact!(A, [LQ]; kwargs...) -> L, Q
lq_compact!(A, [LQ], alg::AbstractAlgorithm) -> L, Q
```

Compute the compact LQ decomposition of the rectangular matrix `A` of size `(m,n)`, such that `A = L * Q` where the matrix `Q` of size `(min(m,n), n)` has orthogonal rows spanning the image of `A'`, and the matrix `L` of size `(m, min(m,n))` is lower triangular.

!!! note
    The bang method `lq_compact!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `LQ` as output.


!!! note
    The compact QR decomposition is equivalent to the full LQ decomposition when `m >= n`. Some algorithms may require `m <= n`.


See also [`lq_full(!)`](@ref lq_full).
