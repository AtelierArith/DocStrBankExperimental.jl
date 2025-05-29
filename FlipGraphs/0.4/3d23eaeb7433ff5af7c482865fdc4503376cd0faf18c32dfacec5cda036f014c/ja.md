```
edges(g::TriangulatedPolygon{T}) :: Vector{SimpleEdge{T}} where T<:Integer
```

`g`のすべての内部エッジのリストを計算して返します。

エッジは方向性がありません。ただし、計算のためにソースとターゲットを定義する必要があります。`TriangulatedPolygon`の場合、ソースは小さいIDを持つ隣接頂点になります。
