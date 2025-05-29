```
mul!(C::AbstractVecOrMat, A::LinearMap, B::AbstractVector, α, β) -> C
mul!(C::AbstractMatrix, A::LinearMap, B::AbstractMatrix, α, β) -> C
```

Combined inplace multiply-add $A B α + C β$. The result is stored in `C` by overwriting it. Note that `C` must not be aliased with either `A` or `B`.

## Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=LinearMap([1.0 2.0; 3.0 4.0]); B=[1.0, 1.0]; C=[1.0, 3.0];

julia> mul!(C, A, B, 100.0, 10.0) === C
true

julia> C
2-element Vector{Float64}:
 310.0
 730.0

julia> A=LinearMap([1.0 2.0; 3.0 4.0]); B=[1.0 1.0; 1.0 1.0]; C=[1.0 2.0; 3.0 4.0];

julia> mul!(C, A, B, 100.0, 10.0) === C
true

julia> C
2×2 Matrix{Float64}:
 310.0  320.0
 730.0  740.0
```
