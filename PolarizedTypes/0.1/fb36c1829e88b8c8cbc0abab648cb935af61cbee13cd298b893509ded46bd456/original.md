```
basis_components([T=Float64,], e::ElectricFieldBasis, b::PolBasis)
```

Returns a static vector that contains the components of the electric field basis vector `e` in terms of the polarization basis `b`. The first argument is optionally the eltype of the static vector.

# Examples

```julia
julia> basis_components(Float64, R(), PolBasis{XPol,Y}())
2-element StaticArraysCore.SVector{2, ComplexF64} with indices SOneTo(2):
 0.7071067811865475 + 0.0im
                0.0 - 0.7071067811865475im

julia> basis_components(R(), PolBasis{XPol,Y}())
2-element StaticArraysCore.SVector{2, ComplexF64} with indices SOneTo(2):
 0.7071067811865475 + 0.0im
                0.0 - 0.7071067811865475im


julia> basis_components(Float64, X(), PolBasis{XPol,Y}())
2-element StaticArraysCore.SVector{2, ComplexF64} with indices SOneTo(2):
 1.0 + 0.0im
 0.0 + 0.0im
```
