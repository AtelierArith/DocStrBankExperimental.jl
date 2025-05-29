```
eig_vals(A; kwargs...) -> D
eig_vals(A, alg::AbstractAlgorithm) -> D
eig_vals!(A, [D]; kwargs...) -> D
eig_vals!(A, [D], alg::AbstractAlgorithm) -> D
```

Compute the list of eigenvalues of `A`.

!!! note
    The bang method `eig_vals!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `D` as output.


!!! note
    Note that [`eig_full`](@ref) and its variants do not assume additional structure on the input,


and therefore will always return complex eigenvalues and eigenvectors. For the real eigenvalue decomposition of symmetric or hermitian operators, see [`eigh_full`](@ref).

See also [`eig_full(!)`](@ref eig_full) and [`eig_trunc(!)`](@ref eig_trunc).
