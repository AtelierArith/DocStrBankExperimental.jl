`interpolate(nodes::Vector{T}, values::Vector{T}, d_nodes::Vector{T}, d_values::Vector{T}, kernel::RK = RK_H1()) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

1Dスプラインを準備して構築します。

# 引数

  * `nodes`: 関数値ノード。
  * `values`: `nodes`ノードでの関数値。
  * `d_nodes`: 関数導関数ノード。
  * `d_values`: `d_nodes`ノードでの関数導関数値。
  * `kernel`: 正常スプラインが構築されるベッセルポテンシャル空間の再生核。次の型の構造体オブジェクトでなければなりません:             スプラインが微分可能な関数として構築される場合は`RK_H1`、             スプラインが二回微分可能な関数として構築される場合は`RK_H2`。

戻り値: `evaluate`関数に渡すことができる完全に初期化された`NormalSpline`オブジェクト。
