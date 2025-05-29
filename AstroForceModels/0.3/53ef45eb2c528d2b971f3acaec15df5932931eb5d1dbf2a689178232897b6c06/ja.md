```
acceleration(u::AbstractArray, p::ComponentVector, t::Number, relativity_model::RelativityModel)
```

宇宙船に作用するsrp加速度を、srpモデルと現在の状態および物体のパラメータに基づいて計算します。

# 引数

  * `u::AbstractArray`: シミュレーションの現在の状態。
  * `p::ComponentVector`: シミュレーションの現在のパラメータ。
  * `t::Number`: シミュレーションの現在の時間。
  * `relativity_model::RelativityModel`: 加速度を計算するために必要な情報を含む相対性モデル構造体。

# 戻り値

  * `acceleration: SVector{3}`: 宇宙船に作用する3次元の相対性加速度。
