```
setTetraParam!(tetrasInfo::Vector{TetrahedraInfo{IT, FT, CT}}) where {IT<:Integer, FT<:AbstractFloat, CT<:Complex}
```

四面体の体積、面外法線ベクトル、面積を計算し、`tetrasInfo` に書き込みます。
