```
relativity_accel(
    u::AbstractArray,
    r_sun::AbstractArray,
    v_sun::AbstractArray,
    μ_body::Number,
    μ_Sun::Number,
    J::AbstractArray;
    c::Number=SPEED_OF_LIGHT / 1E3,
    γ::Number=1.0,
    β::Number=1.0,
    schwartzchild_effect::Bool=true,
    lense_thirring_effect::Bool=true,
    de_Sitter_effect::Bool=true,
)
```

宇宙船に作用する相対論的加速度を、相対論モデルと現在の状態および物体のパラメータに基づいて計算します。

# 引数

  * `u::AbstractArray`: シミュレーションの現在の状態。
  * `r_sun::AbstractArray`: 地球慣性系における太陽の位置。
  * `v_sun::AbstractArray`: 地球慣性系における太陽の速度。
  * `μ_body::Number`: 中心体の重力パラメータ。
  * `μ_Sun::Number`: 太陽の重力パラメータ。 [km^3/s^2]
  * `J::AbstractArray`: 中心体の単位質量あたりの角運動量ベクトル。 [km^3/s^2]
  * `c::Number`: 光の速度 [km/s]
  * `γ::Number`: ポストニュートンパラメータ化パラメータ。一般相対性理論ではγ=1。
  * `β::Number`: ポストニュートンパラメータ化パラメータ。一般相対性理論ではβ=1。
  * `schwartzchild_effect::Bool`: シュワルツシルト相対論効果を含める。
  * `lense_thirring_effect::Bool`: レンズ・ティリング相対論効果を含める。
  * `de_Sitter_effect::Bool`: デ・シッター相対論効果を含める。

# 戻り値

  * `acceleration: SVector{3}`: 宇宙船に作用する3次元の相対論的加速度。
