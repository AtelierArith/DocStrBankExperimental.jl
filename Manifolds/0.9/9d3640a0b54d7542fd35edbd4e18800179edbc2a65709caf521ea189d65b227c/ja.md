```
convert(
    ::Type{Tuple{PoincareHalfSpacePoint,PoincareHalfSpaceTVector}},
    (p,X)::Tuple{PoincareBallPoint,PoincareBallTVector}
)
```

[`PoincareBallPoint`](@ref) `p` と [`PoincareBallTVector`](@ref) `X` を同時に [`PoincareHalfSpacePoint`](@ref) と [`PoincareHalfSpaceTVector`](@ref) に変換します。詳細は [`convert(::Type{PoincareHalfSpacePoint}, ::PoincareBallPoint)`](@ref) と [`convert(::Type{PoincareHalfSpaceTVector}, ::PoincareBallPoint,::PoincareBallTVector)`](@ref) を参照してください。
