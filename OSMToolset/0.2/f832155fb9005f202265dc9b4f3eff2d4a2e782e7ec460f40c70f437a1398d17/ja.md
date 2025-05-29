```
NodeSpatIndex(nodes::AbstractVector{Int64}, llas::AbstractVector{LLA}, refLLA::LLA; node_range::Number=100.0)
```

`nodes` のための空間インデックスを作成し、`llas` LLA 座標を使用して、与えられた `node_range` メートルで ENU 座標の基準として `refLLA` を使用します。
