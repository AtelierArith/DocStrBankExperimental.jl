`prepare(nodes::Vector{T}, d_nodes::Vector{T}, kernel::RK = RK_H1()) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

1Dノーマルスプラインを準備するために、補間問題のグラム行列を構築して因数分解します。`NormalSpline`オブジェクトを初期化します。

# 引数

  * `nodes`: 関数値ノード。
  * `d_nodes`: 関数導関数ノード。
  * `kernel`: ノーマルスプラインが構築されるベッセルポテンシャル空間の再生核。次の型の構造体オブジェクトでなければなりません:             スプラインが微分可能な関数として構築される場合は`RK_H1`、             スプラインが二回微分可能な関数として構築される場合は`RK_H2`。

戻り値: スプラインの初期化を完了するために`construct`関数に渡す必要がある部分的に初期化された`NormalSpline`オブジェクト。
