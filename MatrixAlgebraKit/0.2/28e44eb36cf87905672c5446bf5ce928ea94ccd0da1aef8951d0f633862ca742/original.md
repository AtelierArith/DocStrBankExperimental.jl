```
eigh_full(A; kwargs...) -> D, V
eigh_full(A, alg::AbstractAlgorithm) -> D, V
eigh_full!(A, [DV]; kwargs...) -> D, V
eigh_full!(A, [DV], alg::AbstractAlgorithm) -> D, V
```

Compute the full eigenvalue decomposition of the symmetric or hermitian matrix `A`, such that `A * V = V * D`, where the unitary matrix `V` contains the orthogonal eigenvectors and the real diagonal matrix `D` contains the associated eigenvalues.

!!! note
    The bang method `eigh_full!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `DV` as output.


!!! note
    Note that [`eigh_full`](@ref) and its variants assume additional structure on the input,


and therefore will retain the `eltype` of the input for the eigenvalues and eigenvectors. For generic eigenvalue decompositions, see [`eig_full`](@ref).

See also [`eigh_vals(!)`](@ref eigh_vals) and [`eigh_trunc(!)`](@ref eigh_trunc).
