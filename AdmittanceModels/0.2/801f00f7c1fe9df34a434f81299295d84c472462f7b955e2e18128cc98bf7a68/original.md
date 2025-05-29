```
PSOModel{T, U}(K::U, G::U, C::U, P::U, Q::U, ports::UniqueVector{T}) where {T, U}
PSOModel(K::U, G::U, C::U, P::U, Q::U, ports::AbstractVector{T}) where {T, U}
```

A Positive Second Order model, representing the equations `(K + G∂ₜ + C∂²ₜ)Φ = Px`, `y = Qᵀ∂ₜΦ`.
