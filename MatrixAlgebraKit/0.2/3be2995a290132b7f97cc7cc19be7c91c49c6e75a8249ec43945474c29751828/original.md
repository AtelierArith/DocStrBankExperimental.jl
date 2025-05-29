```
schur_vals(A; kwargs...) -> vals
schur_vals(A, alg::AbstractAlgorithm) -> vals
schur_vals!(A, [vals]; kwargs...) -> vals
schur_vals!(A, [vals], alg::AbstractAlgorithm) -> vals
```

Compute the list of eigenvalues of `A` by computing the Schur decomposition of `A`.

!!! note
    The bang method `schur_vals!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `vals` as output.


See also [`eig_full(!)`](@ref eig_full) and [`eig_trunc(!)`](@ref eig_trunc).
