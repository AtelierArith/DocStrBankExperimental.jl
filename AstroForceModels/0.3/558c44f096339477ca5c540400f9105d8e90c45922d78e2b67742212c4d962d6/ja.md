```
schwartzchild_acceleration(
    u::AbstractArray, μ_body::Number; c::Number=SPEED_OF_LIGHT, γ::Number=1.0, β::Number=1.0
)
```

宇宙船に作用する相対論的加速度を、相対論モデルと現在の状態および物体のパラメータに基づいて計算します。

# 引数

  * `u::AbstractArray`: シミュレーションの現在の状態。
  * `μ_body::Number`: 中心体の重力パラメータ。
  * `c::Number`: 光の速度 [km/s]
  * `γ::Number`: ポストニュートンパラメータ化パラメータ。一般相対性理論ではγ=1。
  * `β::Number`: ポストニュートンパラメータ化パラメータ。一般相対性理論ではβ=1。

# 戻り値

  * `schwartzchild_acceleration: SVector{3}`: 宇宙船に作用する3次元のシュワルツシルト加速度。
