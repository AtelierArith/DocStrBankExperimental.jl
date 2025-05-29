```
mul!(C::AbstractMatrix, A::AbstractMatrix, B::LinearMap) -> C
```

Calculates the matrix representation of `A*B` and stores the result in `C`, overwriting the existing value of `C`. Note that `C` must not be aliased with either `A` or `B`. The computation `C = A*B` is performed via `C' = B'A'`.

## Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=[1.0 1.0; 1.0 1.0]; B=LinearMap([1.0 2.0; 3.0 4.0]); C = similar(A); mul!(C, A, B);

julia> C
2×2 Matrix{Float64}:
 4.0  6.0
 4.0  6.0
```
