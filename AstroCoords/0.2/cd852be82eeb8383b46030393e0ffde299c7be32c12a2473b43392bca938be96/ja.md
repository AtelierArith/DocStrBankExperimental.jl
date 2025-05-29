```
Spherical{T} <: AstroCoord
```

球面軌道要素。軌道の6次元パラメータ化 r - 半径 θ - 面内角 ϕ - 面外角 ṙ - 半径の瞬時変化率 θdot - θの瞬時変化率 ϕdot - ϕの瞬時変化率

コンストラクタ Spherical(r, θ, ϕ, ṙ, ω, Ω) Spherical(X::AbstractArray) Spherical(X::AstroCoord, μ::Number)
