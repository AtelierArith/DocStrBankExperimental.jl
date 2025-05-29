```
setGeosPermittivity!(geosInfo::AbstractVector{VT}, εᵣ::CT = 1.0(1+0im)) where {VT<:VSCellType, CT<:Complex}
setGeosPermittivity!(geosInfo::AbstractVector{VT}, εᵣs::T) where {VT<:VSCellType, T<:AbstractVector}
setGeosPermittivity!(geosInfo::AbstractVector{VT}, εᵣ::CT = 1.0(1+0im)) where {VT<:AbstractVector, CT<:Complex}
```

四面体、六面体の誘電率 `εᵣ` を設定し、同時に媒質のコントラストを設定します。この関数を修正して対応するデータを取得します。
