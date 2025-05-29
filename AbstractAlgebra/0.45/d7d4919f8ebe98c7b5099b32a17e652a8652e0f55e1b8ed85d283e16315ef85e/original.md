```
dense_poly_ring_type(::Type{T}) where T<:NCRingElement
dense_poly_ring_type(::T) where T<:NCRingElement
dense_poly_ring_type(::Type{S}) where S<:NCRing
dense_poly_ring_type(::S) where S<:NCRing
```

The type of univariate polynomial rings with coefficients of type `T` respectively `elem_type(S)`. Implemented via [`dense_poly_type`](@ref).

See also [`mpoly_type`](@ref) and [`mpoly_ring_type`](@ref).

# Examples

```jldoctest
julia> dense_poly_ring_type(AbstractAlgebra.ZZ(1))
AbstractAlgebra.Generic.PolyRing{BigInt}

julia> dense_poly_ring_type(elem_type(AbstractAlgebra.ZZ))
AbstractAlgebra.Generic.PolyRing{BigInt}

julia> dense_poly_ring_type(AbstractAlgebra.ZZ)
AbstractAlgebra.Generic.PolyRing{BigInt}

julia> dense_poly_ring_type(typeof(AbstractAlgebra.ZZ))
AbstractAlgebra.Generic.PolyRing{BigInt}
```
