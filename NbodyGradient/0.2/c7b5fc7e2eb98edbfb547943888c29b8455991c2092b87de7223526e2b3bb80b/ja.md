```
State{T<:AbstractFloat} <: AbstractState
```

シミュレーションの現在の状態。

# フィールド（ユーザーに関連する）

  * `x::Matrix{T}` : 各物体の位置 [次元、物体]。
  * `v::Matrix{T}` : 各物体の速度 [次元、物体]。
  * `t::Vector{T}` : シミュレーションの現在の時間。
  * `m::Vector{T}` : 各物体の質量。
  * `jac_step::Matrix{T}` : 現在のヤコビアン。
  * `dqdt::Vector{T}` : 時間に関する導関数。
