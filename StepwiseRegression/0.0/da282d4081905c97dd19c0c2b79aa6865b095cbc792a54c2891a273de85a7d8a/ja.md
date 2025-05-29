```
infcrit(r)
```

線形回帰モデル `r` の調整済み R²、赤池情報量基準 (AIC)、およびベイズ情報量基準 (BIC) を計算します。

# 引数

  * `r::FixedEffectModel`: 線形回帰モデル

# 戻り値

名前付きタプルを返します：

  * `r2adj::Float64`: 調整済み R²
  * `aic::Float64`: 赤池情報量基準
  * `bic::Float64`: ベイズ情報量基準
