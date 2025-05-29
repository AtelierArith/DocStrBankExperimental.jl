```
r̂θϕInfo(θ::FT = zero(FT), ϕ::FT = zero(FT)) where {FT<:Real}
r̂θϕInfo(θ::∠Info{FT}, ϕ::∠Info{FT}) where {FT<:Real}
r̂θϕInfo(θ::FT, ϕ::∠Info{FT}) where {FT<:Real}
r̂θϕInfo(θ::∠Info{FT}, ϕ::FT) where {FT<:Real}
```

r̂θϕInfo のコンストラクタは、角度 `θ` と `ϕ` を入力として `r̂θϕInfo` インスタンスを構築します。
