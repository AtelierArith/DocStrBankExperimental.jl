```
flip_get_edge!(g::TriangulatedPolygon, src::Integer, dst::Integer) :: Tuple{Int32, Int32}
```

頂点 `src` と `dst` に接続された辺を反転させ、新しく反転された辺の端点を返します。
