```
θϕInfo{FT}(θ::FT = zero(FT), ϕ::FT = zero(FT)) where {FT<:Real}
θϕInfo(θ::FT, ϕ::FT) where {FT<:Real}
θϕInfo{FT}(θ::∠Info{FT}, ϕ::∠Info{FT}) where {FT<:Real}
θϕInfo{FT}(θ::FT, ϕ::∠Info{FT}) where {FT<:Real}
θϕInfo{FT}(θ::∠Info{FT}, ϕ::FT) where {FT<:Real}
```

输入角度 `θ` 和 `ϕ` 构造 `θϕInfo` 实例。
