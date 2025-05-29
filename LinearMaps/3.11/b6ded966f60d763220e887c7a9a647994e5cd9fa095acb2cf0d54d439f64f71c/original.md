```
mul!(C::AbstractMatrix, A::AbstractMatrix, B::LinearMap, α, β) -> C
```

Combined inplace multiply-add $A B α + C β$. The result is stored in `C` by overwriting it. Note that `C` must not be aliased with either `A` or `B`.

## Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=[1.0 1.0; 1.0 1.0]; B=LinearMap([1.0 2.0; 3.0 4.0]); C = copy(A);

julia> mul!(C, A, B, 1, 1)
2×2 Matrix{Float64}:
 5.0  7.0
 5.0  7.0
```
