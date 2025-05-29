```
dense_poly_type(::Type{T}) where T<:NCRingElement
dense_poly_type(::T) where T<:NCRingElement
dense_poly_type(::Type{S}) where S<:NCRing
dense_poly_type(::S) where S<:NCRing
```

The type of univariate polynomials with coefficients of type `T` respectively `elem_type(S)`. Falls back to `Generic.NCPoly{T}` respectively `Generic.Poly{T}`.

See also [`dense_poly_ring_type`](@ref), [`mpoly_type`](@ref) and [`mpoly_ring_type`](@ref).

# Examples

```jldoctest
julia> dense_poly_type(AbstractAlgebra.ZZ(1))
AbstractAlgebra.Generic.Poly{BigInt}

julia> dense_poly_type(elem_type(AbstractAlgebra.ZZ))
AbstractAlgebra.Generic.Poly{BigInt}

julia> dense_poly_type(AbstractAlgebra.ZZ)
AbstractAlgebra.Generic.Poly{BigInt}

julia> dense_poly_type(typeof(AbstractAlgebra.ZZ))
AbstractAlgebra.Generic.Poly{BigInt}
```
