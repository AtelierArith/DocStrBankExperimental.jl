```
*(A::LinearMap, x::AbstractVector)::AbstractVector
```

Compute the action of the linear map `A` on the vector `x`.

## Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=LinearMap([1.0 2.0; 3.0 4.0]); x=[1.0, 1.0];

julia> A*x
2-element Vector{Float64}:
 3.0
 7.0

julia> A(x)
2-element Vector{Float64}:
 3.0
 7.0
```
