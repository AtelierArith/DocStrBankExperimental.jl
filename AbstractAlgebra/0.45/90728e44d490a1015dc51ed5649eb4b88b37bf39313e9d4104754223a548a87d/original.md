```
mpoly_type(::Type{T}) where T<:RingElement
mpoly_type(::T) where T<:RingElement
mpoly_type(::Type{S}) where S<:Ring
mpoly_type(::S) where S<:Ring
```

The type of multivariate polynomials with coefficients of type `T` respectively `elem_type(S)`. Falls back to `Generic.MPoly{T}`.

See also [`mpoly_ring_type`](@ref), [`dense_poly_type`](@ref) and [`dense_poly_ring_type`](@ref).

# Examples

```jldoctest
julia> mpoly_type(AbstractAlgebra.ZZ(1))
AbstractAlgebra.Generic.MPoly{BigInt}

julia> mpoly_type(elem_type(AbstractAlgebra.ZZ))
AbstractAlgebra.Generic.MPoly{BigInt}

julia> mpoly_type(AbstractAlgebra.ZZ)
AbstractAlgebra.Generic.MPoly{BigInt}

julia> mpoly_type(typeof(AbstractAlgebra.ZZ))
AbstractAlgebra.Generic.MPoly{BigInt}
```
