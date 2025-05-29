```julia
mutable struct Pyramid{T} <: ConstrainedDynamics.Shape{T}
```

x-y平面に基づく正方形の`Pyramid`。

  * `wh`: ピラミッドの幅と高さ（ベクトル）。
