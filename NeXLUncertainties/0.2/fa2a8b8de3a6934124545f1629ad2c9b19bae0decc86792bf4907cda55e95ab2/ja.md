```
labelsByType(ty::Type{<:Label}, labels::AbstractVector{<:Label})
labelsByType(types::AbstractVector{DataType}, labels::AbstractVector{<:Label})
```

特定のタイプの `Label` を `Label` のリストからすべて抽出します。2 番目のバージョンは、単一の呼び出しで複数の異なるタイプを抽出します。
