```
square(p::BNGPoint) -> XX::String
```

ポイント `p` が位置する 100 km x 100 km の正方形の名前を含む 2 文字の文字列 `XX` を返します。

```jldoctest
julia> using BritishNationalGrid

julia> BritishNationalGrid.square(BNGPoint(200_000, 1_000_000))
"HX"

```
