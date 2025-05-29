```
NodeSpatIndex(nodes::AbstractVector{Int64}, enus::AbstractVector{ENU}, refLLA::LLA; node_range::Number=100.0)
```

`nodes` の空間インデックスを作成し、`enus` ENU 座標を使用して、与えられた `node_range` メートルで ENU 座標の基準として `refLLA` を使用します。
