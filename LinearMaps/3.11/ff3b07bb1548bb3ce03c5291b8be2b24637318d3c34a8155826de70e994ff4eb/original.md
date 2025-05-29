```
*(x::LinearAlgebra.TransposeAbsVec, A::LinearMap)::TransposeAbsVec
```

Compute the right-action of the linear map `A` on the transpose vector `x` and return a transpose vector.

## Examples

```jldoctest; setup=(using LinearAlgebra, LinearMaps)
julia> A=LinearMap([1.0 2.0; 3.0 4.0]); x=[1.0, 1.0]; transpose(x)*A
1×2 transpose(::Vector{Float64}) with eltype Float64:
 4.0  6.0
```
