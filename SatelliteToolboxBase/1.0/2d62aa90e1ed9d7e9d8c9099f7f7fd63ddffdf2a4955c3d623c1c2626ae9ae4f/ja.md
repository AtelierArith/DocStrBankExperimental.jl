```
struct OrbitStateVector{Tepoch<:Number, T<:Number} <: Orbit{Tepoch, T}
```

軌道の状態ベクトル表現を格納します。

# フィールド

  * `t::Tepoch`: エポック [ユリウス日]。
  * `r::SVector{3, T}`: 位置ベクトル [m]。
  * `v::SVector{3, T}`: 速度ベクトル [m/s]。
  * `a::SVector{3, T}`: 加速度ベクトル [m/s²]。
