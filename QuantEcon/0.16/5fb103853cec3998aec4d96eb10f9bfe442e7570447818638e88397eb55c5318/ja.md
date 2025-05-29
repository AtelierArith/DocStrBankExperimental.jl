ポリシーの値を計算します。

##### パラメータ

  * `ddp::DiscreteDP` : モデルパラメータを含むオブジェクト
  * `sigma::AbstractVector{T<:Integer}` : ポリシールールベクター

##### 戻り値

  * `v_sigma::Array{Float64}` : 長さ `n` の `sigma` の値ベクター。
