`evaluate_gradient(spline::NormalSpline{T, RK}, point::Vector{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

スプラインの指定された位置での勾配を評価します。

# 引数

  * `spline`: `interpolate` または `construct` 関数によって返される `NormalSpline` オブジェクト。
  * `point`: 勾配値が評価される位置。これはサイズ `n` のベクトルであり、`n` はサンプリング空間の次元です。

注意: 再生核 RK_H0 で構築されたスプラインの勾配は、スプラインノードでは存在しません。

戻り値: `Vector{T}` - 指定された位置でのスプラインの勾配。
