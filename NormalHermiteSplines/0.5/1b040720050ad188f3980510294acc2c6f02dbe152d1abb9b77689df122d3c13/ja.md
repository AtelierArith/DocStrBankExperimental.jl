`evaluate_derivative(spline::NormalSpline{T, RK}, point::T) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

1Dスプラインの導関数を`point`位置で評価します。

# 引数

  * `spline`: `interpolate`または`construct`関数によって返される`NormalSpline`オブジェクト。
  * `point`: スプライン導関数を評価する位置。

注意: 再生核RK_H0を用いて構築されたスプラインの導関数は、スプラインノードでは存在しません。

戻り値: `point`位置でのスプライン導関数の値。
