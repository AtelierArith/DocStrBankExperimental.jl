```
setTricoor!( trianglesInfo::Vector{TriangleInfo{IT, FT}}, TriangleMeshData::TriangleMesh{IT, FT}) where {IT<:Integer, FT<:AbstractFloat}
```

在预分配好的三角形数组 `trianglesInfo` 里写入 `TriangleMeshData` 中对应的三角形编号、点坐标、中心位置数据。
