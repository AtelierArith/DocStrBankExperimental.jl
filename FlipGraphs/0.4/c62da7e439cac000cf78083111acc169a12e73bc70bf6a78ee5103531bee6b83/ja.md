```
edges_outer(g::TriangulatedPolygon{T}) :: Vector{SimpleEdge{T}} where T<:Integer
```

`g`のすべての外部エッジのリストを計算して返します。これらは`g`の中でフリップ不可能なエッジです。

エッジは方向を持ちません。ただし、計算のためにソースとターゲットを定義する必要があります。`TriangulatedPolygon`の場合、ソースは小さいIDを持つ隣接頂点になります。
