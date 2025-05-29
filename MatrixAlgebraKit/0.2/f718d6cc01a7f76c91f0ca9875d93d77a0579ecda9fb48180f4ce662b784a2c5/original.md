```
eigh_trunc(A; kwargs...) -> D, V
eigh_trunc(A, alg::AbstractAlgorithm) -> D, V
eigh_trunc!(A, [DV]; kwargs...) -> D, V
eigh_trunc!(A, [DV], alg::AbstractAlgorithm) -> D, V
```

Compute a partial or truncated eigenvalue decomposition of the symmetric or hermitian matrix `A`, such that `A * V ≈ V * D`, where the isometric matrix `V` contains a subset of the orthogonal eigenvectors and the real diagonal matrix `D` contains the associated eigenvalues, selected according to a truncation strategy. 

!!! note
    The bang method `eigh_trunc!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `DV` as output.


!!! note
    Note that [`eigh_full`](@ref) and its variants assume additional structure on the input,


and therefore will retain the `eltype` of the input for the eigenvalues and eigenvectors. For generic eigenvalue decompositions, see [`eig_full`](@ref).

See also [`eigh_full(!)`](@ref eigh_full) and [`eigh_vals(!)`](@ref eigh_vals).
