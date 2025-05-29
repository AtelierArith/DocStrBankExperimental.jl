`estimate_cond(spline::NormalSpline{T, RK}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

グラム行列の条件数の推定を取得します。`spline`オブジェクトが準備されている必要があり、O(N^2)の操作が必要です。（C. Brás, W. Hager, J. Júdice, 行列の条件数を推定するための実行可能な降下アルゴリズムの調査。TOP Vol.20, No.3, 2012。）

# 引数

  * `spline`: `prepare`、`construct`、または`interpolate`関数によって返される`NormalSpline`オブジェクト。

戻り値: グラム行列の条件数の推定。
