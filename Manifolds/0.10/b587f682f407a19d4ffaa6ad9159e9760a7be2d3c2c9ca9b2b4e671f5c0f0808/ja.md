```
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTangentVector}},
    (p,X)::Tuple{PoincareBallPoint,PoincareBallTangentVector}
)
```

[`PoincareBallPoint`](@ref) `p` と [`PoincareBallTangentVector`](@ref) `X` を同時に [`PoincareHalfSpacePoint`](@ref) と [`PoincareHalfSpaceTangentVector`](@ref) に変換します。詳細は [`convert(::Type{PoincareHalfSpacePoint}, ::PoincareBallPoint)`](@ref) と [`convert(::Type{PoincareHalfSpaceTangentVector}, ::PoincareBallPoint,::PoincareBallTangentVector)`](@ref) の式を参照してください。
