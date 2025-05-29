```
setTricoor!( trianglesInfo::Vector{TriangleInfo{IT, FT}}, TriangleMeshData::TriangleMesh{IT, FT}) where {IT<:Integer, FT<:AbstractFloat}
```

在予め割り当てられた三角形配列 `trianglesInfo` に `TriangleMeshData` の対応する三角形番号、点座標、中心位置データを書き込みます。
