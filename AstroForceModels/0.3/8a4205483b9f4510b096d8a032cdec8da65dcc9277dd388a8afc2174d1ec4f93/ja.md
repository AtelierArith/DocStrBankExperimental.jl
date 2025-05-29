```
lense_thirring_acceleration(
    u::AbstractArray,
    μ_body::Number,
    J::AbstractArray;
    c::Number=SPEED_OF_LIGHT,
    γ::Number=1.0,
)
```

宇宙船に作用するレンズ・ティリング相対論的加速度を、相対論モデルと現在の状態、物体のパラメータに基づいて計算します。

# 引数

  * `u::AbstractArray`: シミュレーションの現在の状態。
  * `μ_body::Number`: 中心体の重力パラメータ。
  * `J::AbstractArray`: 中心体の単位質量あたりの角運動量ベクトル。 [km^3/s^2]
  * `c::Number`: 光の速度 [km/s]
  * `γ::Number`: ポスト・ニュートン的パラメータ化パラメータ。一般相対性理論ではγ=1です。

# 戻り値

  * `lense_thirring_acceleration: SVector{3}`: 宇宙船に作用する3次元のレンズ・ティリング加速度。
