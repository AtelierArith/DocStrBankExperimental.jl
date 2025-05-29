```
acceleration(u::AbstractArray, p::ComponentVector, t::Number, grav_model::GravityHarmonicsAstroModel)
```

宇宙船に作用する重力加速度を、重力モデルと現在の状態および物体のパラメータに基づいて計算します。

# 引数

  * `u::AbstractArray`: シミュレーションの現在の状態。
  * `p::ComponentVector`: シミュレーションの現在のパラメータ。
  * `t::Number`: シミュレーションの現在の時間。
  * `gravity_model::GravityHarmonicsAstroModel`: 加速度を計算するために必要な情報を含む重力モデル構造体。

# 戻り値

  * `acceleration: SVector{3}`: 宇宙船に作用する3次元の重力加速度。
