```
earnings_surprises(fmp, symbol)
```

指定されたシンボルの収益サプライズを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Earnings-Surprises](https://site.financialmodelingprep.com/developer/docs/#Earnings-Surprises)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の最新の収益サプライズを取得
data = earnings_surprises(fmp, "AAPL")
```
