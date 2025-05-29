```
mpoly_type(::Type{T}) where T<:RingElement
mpoly_type(::T) where T<:RingElement
mpoly_type(::Type{S}) where S<:Ring
mpoly_type(::S) where S<:Ring
```

型 `T` および `elem_type(S)` の係数を持つ多変数多項式の型。`Generic.MPoly{T}` にフォールバックします。

[`mpoly_ring_type`](@ref)、[`dense_poly_type`](@ref)、および [`dense_poly_ring_type`](@ref) も参照してください。

# 例

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
