```
θϕInfo{FT}(θ::FT = zero(FT), ϕ::FT = zero(FT)) where {FT<:Real}
θϕInfo(θ::FT, ϕ::FT) where {FT<:Real}
θϕInfo{FT}(θ::∠Info{FT}, ϕ::∠Info{FT}) where {FT<:Real}
θϕInfo{FT}(θ::FT, ϕ::∠Info{FT}) where {FT<:Real}
θϕInfo{FT}(θ::∠Info{FT}, ϕ::FT) where {FT<:Real}
```

入力角度 `θ` と `ϕ` を使用して `θϕInfo` インスタンスを構築します。
