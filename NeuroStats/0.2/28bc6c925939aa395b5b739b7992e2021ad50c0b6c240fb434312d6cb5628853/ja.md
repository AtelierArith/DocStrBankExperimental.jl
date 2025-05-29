```
linreg(x, y)
```

二つのベクトル間の線形回帰。

# 引数

  * `x::AbstractVector`
  * `y::AbstractVector`

# 注意事項

予測するには、次のように使用します: `new*x = DataFrame(x = [3.5, 7]); predict(lr, new*x)

# 戻り値

名前付きタプルには以下が含まれます:

  * `lr::StatsModels.TableRegressionModel`: モデル
  * `c::Vector{Float64}`: 回帰係数
  * `se::Vector{Float64}`: 回帰係数の標準誤差
  * `R2::Float64`: R²
  * `R2adj::Float64`: 調整済みR²
  * `aic::Float64`:: 赤池情報量基準 (AIC)
  * `bic::Float64`:: ベイズ情報量基準 (BIC)
  * `lf::Vector{Float64}`: 線形フィット (plot(x, lf))

```
