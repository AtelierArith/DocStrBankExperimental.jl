`evaluate(spline::NormalSpline{T, RK}, points::Matrix{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

スプライン値を`points`で定義された位置で評価します。

# 引数

  * `spline`: `interpolate`または`construct`関数によって返された`NormalSpline`オブジェクト。
  * `points`: スプライン値が評価される位置。これは`n×m`行列である必要があり、`n`はサンプリング空間の次元で、`m`はスプライン値が評価される位置の数です。つまり、行列の各列は1つの位置を定義します。

戻り値: `points`で定義された位置でのスプライン値の`Vector{T}`。
