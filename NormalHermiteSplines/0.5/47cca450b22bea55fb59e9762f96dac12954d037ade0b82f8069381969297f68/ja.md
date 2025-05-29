`get_epsilon(spline::NormalSpline{T, RK}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

スプラインが構築されたベッセルポテンシャル空間の「スケーリングパラメータ」を取得します。

# 引数

  * `spline`: `prepare`、`construct`、または `interpolate` 関数によって返された `NormalSpline` オブジェクト。

返り値: `ε` - 「スケーリングパラメータ」。
