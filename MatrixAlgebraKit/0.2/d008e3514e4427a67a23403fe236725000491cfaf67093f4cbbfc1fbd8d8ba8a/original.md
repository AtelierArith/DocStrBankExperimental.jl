```
lq_full(A; kwargs...) -> L, Q
lq_full(A, alg::AbstractAlgorithm) -> L, Q
lq_full!(A, [LQ]; kwargs...) -> L, Q
lq_full!(A, [LQ], alg::AbstractAlgorithm) -> L, Q
```

Compute the full LQ decomposition of the rectangular matrix `A`, such that `A = L * Q` where `Q` is a square unitary matrix with the same number of rows as `A` and `L` is a lower triangular matrix with the same size as `A`.

!!! note
    The bang method `lq_full!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `LQ` as output.


See also [`lq_compact(!)`](@ref lq_compact).
