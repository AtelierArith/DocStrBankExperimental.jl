`evaluate(point::T, derivative::Int = 0) where T <: AbstractFloat`

ノーマルスプラインとその導関数を評価します。

# 引数

  * `point::T`: スプラインまたはその導関数を評価する位置。
  * `derivative::Int`: `0` - スプライン評価。                    `1` - スプラインの一次導関数の評価。                    `2` - スプラインの二次導関数の評価。

返り値: `point`位置でのスプライン値またはその導関数。
