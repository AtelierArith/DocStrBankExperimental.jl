```
eigh_vals(A; kwargs...) -> D
eigh_vals(A, alg::AbstractAlgorithm) -> D
eigh_vals!(A, [D]; kwargs...) -> D
eigh_vals!(A, [D], alg::AbstractAlgorithm) -> D
```

Compute the list of (real) eigenvalues of the symmetric or hermitian matrix `A`.

!!! note
    The bang method `eigh_vals!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `DV` as output.


!!! note
    Note that [`eigh_full`](@ref) and its variants assume additional structure on the input,


and therefore will retain the `eltype` of the input for the eigenvalues and eigenvectors. For generic eigenvalue decompositions, see [`eig_full`](@ref).

See also [`eigh_full(!)`](@ref eigh_full) and [`eigh_trunc(!)`](@ref eigh_trunc).
