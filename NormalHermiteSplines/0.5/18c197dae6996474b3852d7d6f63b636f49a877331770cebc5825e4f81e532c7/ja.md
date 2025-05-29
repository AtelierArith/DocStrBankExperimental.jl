`estimate_epsilon(nodes::Vector{T}, d_nodes::Vector{T}, kernel::RK = RK_H1()) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

Besselポテンシャル空間の「スケーリングパラメータ」の推定値を取得します。これは、`get_epsilon`関数によって返される結果と一致します。

# 引数

  * `nodes`: 関数値ノード。
  * `d_nodes`: 関数導関数ノード。
  * `kernel`: 通常のスプラインが構築されるBesselポテンシャル空間の再生核。次の型の構造体オブジェクトでなければなりません:             `RK_H1` はスプラインが微分可能な関数として構築される場合、             `RK_H2` はスプラインが二回微分可能な関数として構築される場合。

戻り値: `ε`の推定値。
