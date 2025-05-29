```
r̂θϕInfo(θ::FT = zero(FT), ϕ::FT = zero(FT)) where {FT<:Real}
r̂θϕInfo(θ::∠Info{FT}, ϕ::∠Info{FT}) where {FT<:Real}
r̂θϕInfo(θ::FT, ϕ::∠Info{FT}) where {FT<:Real}
r̂θϕInfo(θ::∠Info{FT}, ϕ::FT) where {FT<:Real}
```

r̂θϕInfo 的构造函数 输入角度 `θ` 和 `ϕ` 构造 `r̂θϕInfo` 实例。
