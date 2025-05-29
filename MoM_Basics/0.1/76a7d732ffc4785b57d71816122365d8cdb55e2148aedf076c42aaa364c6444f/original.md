```
setGeosPermittivity!(geosInfo::AbstractVector{VT}, εᵣ::CT = 1.0(1+0im)) where {VT<:TriangleInfo, CT<:Complex}
```

设置三角形网格介电常数，目前为空派发以方便体面积分方程计算中的多重派发。
