```julia
Particle(ic::Vector{T}) #where ic = [x0, y0, φ0]
Particle(x0, y0, φ0)
Particle(pos::SVector, vel::SVector)
```

初期条件 `x0, y0, φ0` を持つ粒子を作成します。粒子は直線として伝播します。

フィールド `current_cell` は、粒子が現在どの周期的ビリヤードのセルに位置しているかを示します。
