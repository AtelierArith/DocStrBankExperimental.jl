`get_cond(nodes::Matrix{T}, d_nodes::Matrix{T}, es::Matrix{T}, kernel::RK = RK_H1()) where {T <: AbstractFloat, RK <: ReproducingKernel_1}`

グラム行列のスペクトル条件数の値を取得します。これは行列のSVD分解によって得られ、$O(N^3)$の操作を必要とします。

# 引数

  * `nodes`: 関数値ノード。          これは`n×n_1`行列である必要があり、`n`はサンプリング空間の次元で、          `n_1`は関数値ノードの数です。           これは、行列の各列が1つのノードを定義することを意味します。
  * `d_nodes`: 関数の方向微分ノード。            これは`n×n_2`行列である必要があり、`n`はサンプリング空間の次元で、            `n_2`は関数の方向微分ノードの数です。
  * `es`: 関数の方向微分の方向。       これは`n×n_2`行列である必要があり、`n`はサンプリング空間の次元で、       `n_2`は関数の方向微分ノードの数です。       これは、行列の各列が関数の方向微分の1つの方向を定義することを意味します。
  * `kernel`: 正規スプラインが構築されるベッセルポテンシャル空間の再生核。           これは次の型の構造体オブジェクトである必要があります:             スプラインが微分可能な関数として構築される場合は`RK_H1`、             スプラインが2回微分可能な関数として構築される場合は`RK_H2`。

戻り値: グラム行列のスペクトル条件数の値。
