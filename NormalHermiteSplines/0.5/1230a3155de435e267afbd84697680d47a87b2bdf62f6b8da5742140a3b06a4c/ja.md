`construct(spline::NormalSpline{T, RK}, values::Vector{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

スプラインを構築し、その係数を計算して`NormalSpline`オブジェクトを完全に初期化します。

# 引数

  * `spline`: `prepare`関数によって返された部分的に初期化された`NormalSpline`オブジェクト。
  * `values`: `nodes`ノードでの関数値。

戻り値: データを必要な点に補間するために`evaluate`関数に渡すことができる完全に初期化された`NormalSpline`オブジェクト。
