```
has_a_path(g::AbstractGraph, U::Vector, V::VectorOrVertex, exclude_vertices::AbstractVector = T[], nbs=Graphs.outneighbors)
```

UとVを接続する（半有向）パスが`exclude_vertices`を通らずに存在するかを確認します。ここで、`nbs=Graphs.outneighbors`は移動の方向を決定します。
