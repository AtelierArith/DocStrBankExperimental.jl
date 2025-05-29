```
eigen(A::SymmetricTensor{2})
```

Compute the eigenvalues and eigenvectors of a symmetric second order tensor and return an `Eigen` object. The eigenvalues are stored in a `Vec`, sorted in ascending order. The corresponding eigenvectors are stored as the columns of a `Tensor`.

See [`eigvals`](@ref) and [`eigvecs`](@ref).

# Examples

```jldoctest
julia> A = rand(SymmetricTensor{2, 2});

julia> E = eigen(A);

julia> E.values
2-element Vec{2, Float64}:
 -0.27938877799585415
  0.8239521616782797

julia> E.vectors
2×2 Tensor{2, 2, Float64, 4}:
 -0.671814  0.74072
  0.74072   0.671814
```
