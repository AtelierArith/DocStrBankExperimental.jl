```
mpoly_ring_type(::Type{T}) where T<:RingElement
mpoly_ring_type(::T) where T<:RingElement
mpoly_ring_type(::Type{S}) where S<:Ring
mpoly_ring_type(::S) where S<:Ring
```

The type of multivariate polynomial rings with coefficients of type `T` respectively `elem_type(S)`. Implemented via [`mpoly_type`](@ref).

See also [`dense_poly_type`](@ref) and [`dense_poly_ring_type`](@ref).

# Examples

```jldoctest
julia> mpoly_ring_type(AbstractAlgebra.ZZ(1))
AbstractAlgebra.Generic.MPolyRing{BigInt}

julia> mpoly_ring_type(elem_type(AbstractAlgebra.ZZ))
AbstractAlgebra.Generic.MPolyRing{BigInt}

julia> mpoly_ring_type(AbstractAlgebra.ZZ)
AbstractAlgebra.Generic.MPolyRing{BigInt}

julia> mpoly_ring_type(typeof(AbstractAlgebra.ZZ))
AbstractAlgebra.Generic.MPolyRing{BigInt}
```
