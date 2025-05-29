```
setHexaCoor!( tetrasInfo::Vector{TetrahedraInfo{IT, FT, CT}}, tetraMeshData::TetrahedraMesh{IT, FT}) where {IT<:Integer, FT<:AbstractFloat, CT<:Complex}
```

在予め割り当てられた四面体配列 `tetrasInfo` に `tetraMeshData` の対応する四面体番号、点の座標、中心位置データを書き込みます。
