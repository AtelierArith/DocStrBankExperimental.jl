`evaluate_one(spline::NormalSpline{T, RK}, point::Vector{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

スプライン値を`point`位置で評価します。

# 引数

  * `spline`: `interpolate`または`construct`関数によって返される`NormalSpline`オブジェクト。
  * `point`: スプライン値が評価される位置。これはサイズ`n`のベクトルである必要があり、`n`はサンプリング空間の次元です。

戻り値: `point`で定義された位置のスプライン値。
