```
coordinates(@nospecialize(ids::IDS), field::Symbol; coord_leaves::Union{Nothing,Vector{<:Union{Nothing,Symbol}}}=nothing)
```

座標名のリストと、データ構造内の値のリストを返します。

データに座標がない場合、座標値は `nothing` になります。

データ構造内で座標が欠落している場合、座標値は `missing` になります。

`coord_leaves` を使用して、特定のフィールドの座標を取得することを上書きします。
