`estimate_epsilon(nodes::Vector{T}, kernel::RK = RK_H0()) where {T <: AbstractFloat, RK <: ReproducingKernel_0}`

Besselポテンシャル空間の「スケーリングパラメータ」の推定値を取得します。これは、`get_epsilon`関数が返す結果と一致します。

# 引数

  * `nodes`: 関数値ノード。
  * `kernel`: 正常スプラインが構築されるBesselポテンシャル空間の再生核。次の型の構造体オブジェクトでなければなりません:             スプラインが連続関数として構築される場合は`RK_H0`、             スプラインが微分可能関数として構築される場合は`RK_H1`、             スプラインが二回微分可能関数として構築される場合は`RK_H2`。

戻り値: `ε`の推定値。
