```
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTVector}},
    (p,X)::Tuple{HyperboloidPoint,HyperboloidTVector}
)
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTVector}},
    (p, X)::Tuple{T,T},
) where {T <: AbstractVector}
```

[`PoincareHalfSpacePoint`](@ref) `p` と [`PoincareHalfSpaceTVector`](@ref) `X` を [`PoincareBallPoint`](@ref) と [`PoincareBallTVector`](@ref) に同時に変換します。詳細は [`convert(::Type{PoincareBallPoint}, ::PoincareHalfSpacePoint)`](@ref) と [`convert(::Type{PoincareBallTVector}, ::PoincareHalfSpacePoint, ::PoincareHalfSpaceTVector)`](@ref) を参照してください。
