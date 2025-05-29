```
de_Sitter_acceleration(
    u::AbstractArray,
    r_sun::AbstractArray,
    v_sun::AbstractArray,
    μ_Sun::Number;
    c::Number=SPEED_OF_LIGHT,
    γ::Number=1.0,
)
```

宇宙船に作用する相対論的加速度を、相対論モデルと現在の状態および物体のパラメータに基づいて計算します。

# 引数

  * `u::AbstractArray`: シミュレーションの現在の状態。
  * `r_sun::AbstractArray`: 地球慣性系における太陽の位置。
  * `v_sun::AbstractArray`: 地球慣性系における太陽の速度。
  * `μ_Sun::Number`: 太陽の重力パラメータ。 [km^3/s^2]
  * `c::Number`: 光の速度 [km/s]
  * `γ::Number`: ポストニュートンパラメータ化パラメータ。一般相対性理論ではγ=1。

# 戻り値

  * `de_Sitter_acceleration: SVector{3}`: 宇宙船に作用する3次元のデシッター加速度。
