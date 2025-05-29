```
edges_inner(g::TriangulatedPolygon{T}) :: Vector{SimpleEdge{T}} where T<:Integer
```

`g`のすべてのエッジのリストを計算して返します。これらは`g`のフリッパブルエッジです。

エッジは無向です。ただし、計算のためにソースとターゲットを定義する必要があります。`TriangulatedPolygon`の場合、ソースは小さいIDを持つ隣接頂点になります。
