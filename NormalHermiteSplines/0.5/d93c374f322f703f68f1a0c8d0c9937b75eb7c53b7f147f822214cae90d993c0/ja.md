`estimate_accuracy(spline::NormalSpline{T, RK}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

補間結果の精度を残差を分析することで評価します。

# 引数

  * `spline`: `construct` または `interpolate` 関数によって返される `NormalSpline` オブジェクト。

戻り値: 補間結果の有効数字の推定値。
