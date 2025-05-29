`evaluate_one(spline::NormalSpline{T, RK}, point::T) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

1Dスプライン値を`point`位置で評価します。

# 引数

  * `spline`: `interpolate`または`construct`関数によって返された`NormalSpline`オブジェクト。
  * `point`: スプライン値が評価される位置。

戻り値: `point`位置でのスプライン値。
