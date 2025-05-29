```
Cylindrical{T} <: AstroCoord
```

円筒座標軌道要素。軌道の6次元パラメータ化 ρ - 面内半径 θ - 面内角 z - 面外距離 ρdot - 面内半径の瞬時変化率 θdot - θの瞬時変化率 ż - zの瞬時変化率

コンストラクタ Cylindrical(r, θ, z, ṙ, θdot, ż) Cylindrical(X::AbstractArray) Cylindrical(X::AstroCoord, μ::Number)
