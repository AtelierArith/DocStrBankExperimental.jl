```
≫(a::AbstractInterval, b::AbstractInterval) -> Bool
greater_than_disjoint(a::AbstractInterval, b::AbstractInterval) -> Bool
```

大なりかつ非重複比較演算子。`a` が `b` より大きく、かつそれらが非重複（重なっていない）場合に `true` を返します。

```
julia> 10..20 ≫ 0..10
false

julia> 11..20 ≫ 0..10
true
```
