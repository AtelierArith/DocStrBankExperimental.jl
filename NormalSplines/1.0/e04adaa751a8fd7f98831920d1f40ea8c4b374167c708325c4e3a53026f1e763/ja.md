`evaluate(points::Vector{T}, derivative::Int = 0) where T <: AbstractFloat`

ノーマルスプラインとその導関数を評価します。

# 引数

  * `points::Vector{T}`: スプラインまたはその導関数を評価する位置。
  * `derivative::Int`: `0` - スプライン評価。                    `1` - スプラインの第一導関数の評価。                    `2` - スプラインの第二導関数の評価。

戻り値: `Vector{T}` のスプライン値または `points` で定義された位置でのその導関数。
