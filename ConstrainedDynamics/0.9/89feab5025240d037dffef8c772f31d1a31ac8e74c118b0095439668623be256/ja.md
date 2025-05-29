```julia
mutable struct Box{T} <: ConstrainedDynamics.Shape{T}
```

`Box`。

# 重要な属性

  * `xyz`: x、y、z方向のボックスサイズ（ベクトル）。
