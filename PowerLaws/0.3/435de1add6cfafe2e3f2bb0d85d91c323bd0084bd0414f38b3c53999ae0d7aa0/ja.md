bootstrap

パワー法則分布のパラメータを推定するためのブートストラップ法。xminの推定値の不確実性を定量化するために、ブートストラップ法を使用できます。詳細はこの文書 [Power-law distributions in empirical data](http://arxiv.org/pdf/0706.1062v2.pdf) にあります。

# 引数

  * `data::AbstractArray`: テストするデータ。
  * `d::UnivariateDistribution`: テストする分布（`ContinuousPowerLaw` または `DiscretePowerLaw`）。
  * `no_of_sims::Int64`: シミュレーションの数。デフォルトは `10`。
  * `xmins::AbstractArray`: テストするxminsの配列、デフォルトは `data`。
  * `xmax::Int64`: 考慮するデータの最大値。デフォルトは `1e5`。
  * `seed::Int64`: ランダム数生成器のシード。デフォルトは `0`。

# 戻り値

  * `statistic::Array{Tuple{UnivariateDistribution, Float64}}`: データと分布の間のコルモゴロフ-スミルノフ距離を含む分布のタプルの配列。
