```julia
mutable struct Cylinder{T} <: ConstrainedDynamics.Shape{T}
```

z軸に沿った`Cylinder`。

# 重要な属性

  * `rh`: シリンダーの半径と高さ（ベクトル）。
