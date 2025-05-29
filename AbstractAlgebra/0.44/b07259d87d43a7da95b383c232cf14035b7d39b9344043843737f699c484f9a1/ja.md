```
mpoly_ring_type(::Type{T}) where T<:RingElement
mpoly_ring_type(::T) where T<:RingElement
mpoly_ring_type(::Type{S}) where S<:Ring
mpoly_ring_type(::S) where S<:Ring

型 `T` および `elem_type(S)` の係数を持つ多変数多項式環の型。 [`mpoly_type`](@ref) を介して実装されています。

[`dense_poly_type`](@ref) および [`dense_poly_ring_type`](@ref) も参照してください。

# 例

```

jldoctest julia> mpoly*ring*type(AbstractAlgebra.ZZ(1)) AbstractAlgebra.Generic.MPolyRing{BigInt}

julia> mpoly*ring*type(elem_type(AbstractAlgebra.ZZ)) AbstractAlgebra.Generic.MPolyRing{BigInt}

julia> mpoly*ring*type(AbstractAlgebra.ZZ) AbstractAlgebra.Generic.MPolyRing{BigInt}

julia> mpoly*ring*type(typeof(AbstractAlgebra.ZZ)) AbstractAlgebra.Generic.MPolyRing{BigInt} ```
