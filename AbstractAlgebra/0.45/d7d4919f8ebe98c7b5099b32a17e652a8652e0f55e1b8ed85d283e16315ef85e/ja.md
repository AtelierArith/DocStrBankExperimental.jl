```
dense_poly_ring_type(::Type{T}) where T<:NCRingElement
dense_poly_ring_type(::T) where T<:NCRingElement
dense_poly_ring_type(::Type{S}) where S<:NCRing
dense_poly_ring_type(::S) where S<:NCRing
```

型 `T` および `elem_type(S)` の係数を持つ一変数多項式環の型。 [`dense_poly_type`](@ref) を介して実装されています。

[`mpoly_type`](@ref) および [`mpoly_ring_type`](@ref) も参照してください。

# 例

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
