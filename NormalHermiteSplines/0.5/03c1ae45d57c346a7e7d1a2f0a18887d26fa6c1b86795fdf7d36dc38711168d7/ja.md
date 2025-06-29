`estimate_epsilon(nodes::Matrix{T}, kernel::RK = RK_H0()) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Besselポテンシャル空間の「スケーリングパラメータ」の推定値を取得します。これは、`get_epsilon`関数によって返される結果と一致します。

# 引数

  * `nodes`: 関数値ノード。          これは `n×n_1` 行列である必要があり、`n` はサンプリング空間の次元          で、`n_1` は関数値ノードの数です。          これは、行列の各列が1つのノードを定義することを意味します。
  * `kernel`: 通常のスプラインが構築されるBesselポテンシャル空間の再生核。          これは次の型の構造体オブジェクトである必要があります:            スプラインが連続関数として構築される場合は `RK_H0`、            スプラインが微分可能な関数として構築される場合は `RK_H1`、            スプラインが2回微分可能な関数として構築される場合は `RK_H2`。

戻り値: `ε`の推定値。
