```
dense_poly_type(::Type{T}) where T<:NCRingElement
dense_poly_type(::T) where T<:NCRingElement
dense_poly_type(::Type{S}) where S<:NCRing
dense_poly_type(::S) where S<:NCRing
```

型 `T` または `elem_type(S)` の係数を持つ一変数多項式の型。`Generic.NCPoly{T}` または `Generic.Poly{T}` にフォールバックします。

[`dense_poly_ring_type`](@ref)、[`mpoly_type`](@ref)、および [`mpoly_ring_type`](@ref) も参照してください。

# 例

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
