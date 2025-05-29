```
*(x::LinearAlgebra.AdjointAbsVec, A::LinearMap)::AdjointAbsVec
```

Compute the right-action of the linear map `A` on the adjoint vector `x` and return an adjoint vector.

## Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=LinearMap([1.0 2.0; 3.0 4.0]); x=[1.0, 1.0]; x'A
1×2 adjoint(::Vector{Float64}) with eltype Float64:
 4.0  6.0
```
