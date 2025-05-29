```
infcrit(m)
```

線形回帰モデル `m` の R²、調整済み R²、赤池情報量基準 (AIC)、およびベイズ情報量基準 (BIC) を計算します。

# 引数

  * `m::StatsModels.TableRegressionModel`: 線形回帰モデル

# 戻り値

名前付きタプルを含む:

  * `R2::Float64`
  * `R2adj::Float64`
  * `bic::Float64`
  * `bic::Float64`
