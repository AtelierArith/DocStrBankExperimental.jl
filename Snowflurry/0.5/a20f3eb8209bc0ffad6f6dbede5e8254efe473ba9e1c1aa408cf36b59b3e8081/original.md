```
eigen(A::AbstractOperator)
```

Compute the eigenvalue decomposition of Operator `A` and return an `Eigen` factorization object `F`. Eigenvalues are found in `F.values` while eigenvectors are found in the matrix `F.vectors`. Each column of this matrix corresponds to an eigenvector. The `i`th eigenvector is extracted by calling `F.vectors[:, i]`.

# Examples

```jldoctest
julia> X = sigma_x()
(2,2)-element Snowflurry.AntiDiagonalOperator:
Underlying data type: ComplexF64:
    .    1.0 + 0.0im
    1.0 + 0.0im    .

julia> F = eigen(X);

julia> eigenvalues = F.values
2-element Vector{Float64}:
 -1.0
  1.0

julia> eigenvector_1 = F.vectors[:, 1]
2-element Vector{ComplexF64}:
 -0.7071067811865475 + 0.0im
  0.7071067811865475 + 0.0im
```
