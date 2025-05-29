```julia
MagneticParticle(ic::AbstractVector{T}, ω::Real) # where ic = [x0, y0, φ0]
MagneticParticle(x0, y0, φ0, ω)
MagneticParticle(pos::SVector, vel::SVector, ω)
MagneticParticle(p::AbstractParticle, ω)
```

初期条件 `x0, y0, φ0` と角速度 `ω` を持つ*磁気*粒子を作成します。これは直線ではなく円として伝播し、半径は `1/abs(ω)` です。

フィールド `current_cell` は、粒子が現在どの周期的ビリヤードのセルに位置しているかを示します。
