```
edge_regions(full_domain::CartesianIndices, axis::Int, nhalo::Int, nedge::Int)
```

ハロ領域の境界に沿って `full_domain` からサブドメインを抽出します（厚さは `nhalo` で定義されます）、厚さは `nedge` です。
