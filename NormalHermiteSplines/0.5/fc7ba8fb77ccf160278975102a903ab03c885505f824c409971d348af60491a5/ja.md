`construct(spline::NormalSpline{T, RK}, values::Vector{T}, d_values::Vector{T}) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

スプラインを構築するために、その係数を計算し、`NormalSpline`オブジェクトを完全に初期化します。

# 引数

  * `spline`: `prepare`関数によって返された部分的に初期化された`NormalSpline`オブジェクト。
  * `values`: `nodes`ノードでの関数値。
  * `d_values`: `d_nodes`ノードでの関数の方向導関数値。

戻り値: データを必要なポイントに補間するために`evaluate`関数に渡すことができる完全に初期化された`NormalSpline`オブジェクト。
