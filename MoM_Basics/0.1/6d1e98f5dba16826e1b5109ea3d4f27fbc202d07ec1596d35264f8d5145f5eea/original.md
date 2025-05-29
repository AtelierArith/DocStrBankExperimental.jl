```
setTetraParam!(tetrasInfo::Vector{TetrahedraInfo{IT, FT, CT}}) where {IT<:Integer, FT<:AbstractFloat, CT<:Complex}
```

计算四面体体积、面外法向量、面积，并写入 `tetrasInfo` 。
