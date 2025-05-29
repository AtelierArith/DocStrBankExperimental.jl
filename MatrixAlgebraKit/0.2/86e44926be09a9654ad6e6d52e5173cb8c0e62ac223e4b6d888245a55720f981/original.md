```
eig_full(A; kwargs...) -> D, V
eig_full(A, alg::AbstractAlgorithm) -> D, V
eig_full!(A, [DV]; kwargs...) -> D, V
eig_full!(A, [DV], alg::AbstractAlgorithm) -> D, V
```

Compute the full eigenvalue decomposition of the square matrix `A`, such that `A * V = V * D`, where the invertible matrix `V` contains the eigenvectors and the diagonal matrix `D` contains the associated eigenvalues.

!!! note
    The bang method `eig_full!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `DV` as output.


!!! note
    Note that [`eig_full`](@ref) and its variants do not assume additional structure on the input,


and therefore will always return complex eigenvalues and eigenvectors. For the real eigenvalue decomposition of symmetric or hermitian operators, see [`eigh_full`](@ref).

See also [`eig_vals(!)`](@ref eig_vals) and [`eig_trunc(!)`](@ref eig_trunc).
