```
setGeosPermittivity!(geosInfo::AbstractVector{VT}, εᵣ::CT = 1.0(1+0im)) where {VT<:TriangleInfo, CT<:Complex}
```

三角形メッシュの誘電率を設定します。現在は空のディスパッチで、体積積分方程式の計算における多重ディスパッチを容易にするためです。
