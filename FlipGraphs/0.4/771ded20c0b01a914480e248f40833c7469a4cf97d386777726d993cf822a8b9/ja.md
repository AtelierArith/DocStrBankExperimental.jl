```
relative_degrees(g::TriangulatedPolygon, U::Vector{<:Integer}, V::Vector{<:Integer}) :: Vector{<:Integer}
```

`U`の各頂点について、`V`のエッジにも接続されている接続エッジの数をカウントします。
