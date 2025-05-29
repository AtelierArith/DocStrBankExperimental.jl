```
build_dynamics_model(u::AbstractArray, p::ComponentVector, t::Number, models::AbstractArray{AbstractAstroForceModel})
```

宇宙船に作用する全体の加速度を計算するための便利な関数です。

# 引数

  * `u::AbstractArray`: シミュレーションの現在の状態。
  * `p::ComponentVector`: シミュレーションの現在のパラメータ。
  * `t::Number`: シミュレーションの現在の時間。
  * `models::AbstractArray{AbstractAstroForceModel}`: 宇宙船に作用する加速度モデルの配列。

# 戻り値

  * `acceleration: SVector{3}`: 宇宙船に作用する3次元の抗力加速度。
