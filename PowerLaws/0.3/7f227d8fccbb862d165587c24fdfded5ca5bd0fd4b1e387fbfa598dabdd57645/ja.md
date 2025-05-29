bootstrap_p

パワー法則分布が妥当であるかどうかを判断するためのブートストラップ仮説検定を実行します。Rの[poweRlaw](http://arxiv.org/pdf/1407.3492v1.pdf)ドキュメントに触発されています。

# 引数

  * `data::AbstractArray`: テストするデータ。
  * `d::UnivariateDistribution`: テストする分布（`ContinuousPowerLaw`または`DiscretePowerLaw`）。
  * `no_of_sims::Int64`: シミュレーションの数。デフォルトは`10`。
  * `xmins::AbstractArray`: テストするxminsの配列、デフォルトは`data`。
  * `xmax::Int64`: 考慮するデータの最大値。デフォルトは`1e5`。
  * `seed::Int64`: ランダム数生成器のシード。デフォルトは`0`。

# 戻り値

  * `statistic::Array{Tuple{UnivariateDistribution, Float64}}`: データと分布の間のコルモゴロフ-スミルノフ距離を含む分布のタプルの配列。
  * `P::Float64`: 仮説検定のp値。
