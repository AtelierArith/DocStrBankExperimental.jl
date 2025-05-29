```
owners_earnings(fmp, symbol)
```

指定されたシンボルのオーナーの収益を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Owners-Earnings](https://site.financialmodelingprep.com/developer/docs/#Stock-Financial-scores)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL のオーナーの収益を取得
data = owners_earnings(fmp, "AAPL")
```
