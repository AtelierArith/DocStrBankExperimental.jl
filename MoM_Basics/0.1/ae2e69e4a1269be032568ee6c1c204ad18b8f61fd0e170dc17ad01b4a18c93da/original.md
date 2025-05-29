```
setHexaCoor!( tetrasInfo::Vector{TetrahedraInfo{IT, FT, CT}}, tetraMeshData::TetrahedraMesh{IT, FT}) where {IT<:Integer, FT<:AbstractFloat, CT<:Complex}
```

在预分配好的四面体数组 `tetrasInfo` 里写入 `tetraMeshData` 中对应的四面体编号、点坐标、中心位置数据。
