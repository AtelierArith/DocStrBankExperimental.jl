```
RingIncluding{D} <: AbstractVector{OffsetVertexIterator{D}}
```

特定の頂点 `PeriodicVertex{D}(i)` を含む `PeriodicGraph{D}` のリングのリスト。

このオブジェクトは反復可能で、整数によってインデックス指定できます：型 `RingIncluding{D}` の `ri` に対して、`ri[j]` は頂点 `i` を含む `j` 番目のリングの頂点を反復するものです。
