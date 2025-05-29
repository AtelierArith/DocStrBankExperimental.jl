```
acceleration(u::AbstractArray, p::ComponentVector, t::Number, third_body_model::ThirdBodyModel)
```

宇宙船に作用する抗力加速度を、抗力モデルと現在の状態および物体のパラメータに基づいて計算します。

# 引数

  * `u::AbstractArray`: シミュレーションの現在の状態。
  * `p::ComponentVector`: シミュレーションの現在のパラメータ。
  * `t::Number`: シミュレーションの現在の時間。
  * `third_body_model::ThirdBodyModel`: 加速度を計算するために必要な情報を含む第三者モデル構造体。

# 戻り値

  * `acceleration: SVector{3}`: 宇宙船に作用する3次元のSRP加速度。
