```
eig_trunc(A; kwargs...) -> D, V
eig_trunc(A, alg::AbstractAlgorithm) -> D, V
eig_trunc!(A, [DV]; kwargs...) -> D, V
eig_trunc!(A, [DV], alg::AbstractAlgorithm) -> D, V
```

Compute a partial or truncated eigenvalue decomposition of the matrix `A`, such that `A * V ≈ V * D`, where the (possibly rectangular) matrix `V` contains  a subset of eigenvectors and the diagonal matrix `D` contains the associated eigenvalues, selected according to a truncation strategy.

!!! note
    The bang method `eig_trunc!` optionally accepts the output structure and possibly destroys the input matrix `A`. Always use the return value of the function as it may not always be possible to use the provided `DV` as output.


!!! note
    Note that [`eig_full`](@ref) and its variants do not assume additional structure on the input,


and therefore will always return complex eigenvalues and eigenvectors. For the real eigenvalue decomposition of symmetric or hermitian operators, see [`eigh_full`](@ref).

See also [`eig_full(!)`](@ref eig_full) and [`eig_vals(!)`](@ref eig_vals).
