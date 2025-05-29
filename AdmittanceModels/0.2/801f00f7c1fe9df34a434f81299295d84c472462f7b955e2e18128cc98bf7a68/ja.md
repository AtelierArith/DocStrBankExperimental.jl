```
PSOModel{T, U}(K::U, G::U, C::U, P::U, Q::U, ports::UniqueVector{T}) where {T, U}
PSOModel(K::U, G::U, C::U, P::U, Q::U, ports::AbstractVector{T}) where {T, U}
```

正の二次モデルで、方程式 `(K + G∂ₜ + C∂²ₜ)Φ = Px`、`y = Qᵀ∂ₜΦ` を表します。
