```
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTangentVector}},
    (p,X)::Tuple{HyperboloidPoint,HyperboloidTangentVector}
)
convert(
    ::Type{Tuple{PoincareBallPoint,PoincareBallTangentVector}},
    (p, X)::Tuple{T,T},
) where {T <: AbstractVector}
```

[`PoincareHalfSpacePoint`](@ref) `p` と [`PoincareHalfSpaceTangentVector`](@ref) `X` を同時に [`PoincareBallPoint`](@ref) と [`PoincareBallTangentVector`](@ref) に変換します。詳細は [`convert(::Type{PoincareBallPoint}, ::PoincareHalfSpacePoint)`](@ref) と [`convert(::Type{PoincareBallTangentVector}, ::PoincareHalfSpacePoint, ::PoincareHalfSpaceTangentVector)`](@ref) を参照してください。
