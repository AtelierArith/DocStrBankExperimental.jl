```
setGeosPermittivity!(geosInfo::AbstractVector{VT}, εᵣ::CT = 1.0(1+0im)) where {VT<:VSCellType, CT<:Complex}
setGeosPermittivity!(geosInfo::AbstractVector{VT}, εᵣs::T) where {VT<:VSCellType, T<:AbstractVector}
setGeosPermittivity!(geosInfo::AbstractVector{VT}, εᵣ::CT = 1.0(1+0im)) where {VT<:AbstractVector, CT<:Complex}
```

设置四面体、六面体的介电常数 `εᵣ` ，并同时设置介质对比度，修改此函数以得到对应的数据。
