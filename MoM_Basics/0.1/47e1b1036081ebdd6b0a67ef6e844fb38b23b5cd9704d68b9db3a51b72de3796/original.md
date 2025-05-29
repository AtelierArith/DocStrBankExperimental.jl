```
setHexaParam!(hexasInfo::Vector{HexahedraInfo{IT, FT, CT}}) where {IT<:Integer, FT<:AbstractFloat, CT<:Complex}
```

计算六面体体积、面外法向量、面积，并写入 `hexasInfo` 。
