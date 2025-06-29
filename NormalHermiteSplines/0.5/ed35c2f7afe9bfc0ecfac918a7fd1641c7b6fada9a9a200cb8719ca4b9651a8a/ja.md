`prepare(nodes::Matrix{T}, kernel::RK = RK_H0()) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

スプラインを準備するために、補間問題のグラム行列を構築して因数分解します。`NormalSpline`オブジェクトを初期化します。

# 引数

  * `nodes`: 関数値ノード。これは `n×n_1` 行列である必要があり、`n` はサンプリング空間の次元で、`n_1` は関数値ノードの数です。つまり、行列の各列は1つのノードを定義します。
  * `kernel`: 正常スプラインが構築されるベッセルポテンシャル空間の再生核。次のタイプの構造体オブジェクトである必要があります:             `RK_H0` はスプラインが連続関数として構築される場合、             `RK_H1` はスプラインが微分可能関数として構築される場合、             `RK_H2` はスプラインが2回微分可能関数として構築される場合。

戻り値: スプラインの初期化を完了するために `construct` 関数に渡す必要がある部分的に初期化された `NormalSpline` オブジェクト。
