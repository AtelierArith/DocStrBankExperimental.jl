`evaluate(spline::NormalSpline{T, RK}, points::Vector{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

スプラインの値を`points`の位置で評価します。

# 引数

  * `spline`: `interpolate`または`construct`関数によって返される`NormalSpline`オブジェクト。
  * `points`: スプライン値が評価される位置。これはサイズ`m`のベクトルであり、`m`は評価ポイントの数です。

戻り値: `point`位置でのスプライン値。
