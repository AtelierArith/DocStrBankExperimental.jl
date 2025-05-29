```
acceleration(u::AbstractArray, p::ComponentVector, t::Number, srp_model::SRPAstroModel)
```

宇宙船に作用するsrp加速度を、srpモデルと現在の状態および物体のパラメータを考慮して計算します。

# 引数

  * `u::AbstractArray`: シミュレーションの現在の状態。
  * `p::ComponentVector`: シミュレーションの現在のパラメータ。
  * `t::Number`: シミュレーションの現在の時間。
  * `srp_model::SRPAstroModel`: 加速度を計算するために必要な情報を含むSRPモデル構造体。

# 戻り値

  * `acceleration: SVector{3}`: 宇宙船に作用する3次元のsrp加速度。
