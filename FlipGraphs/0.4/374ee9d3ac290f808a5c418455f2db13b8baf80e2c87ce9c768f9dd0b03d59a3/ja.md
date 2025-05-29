```
is_isomorphic(g1::TriangulatedPolygon, g2::TriangulatedPolygon, permutations::Vector{Vector{T}}) where T<:Integer
```

`g2`が`g1`と同型であるかを、`permutations`のいずれかによる頂点の再ラベリングまで確認します。
