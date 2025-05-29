```
mutual_fund_holders(fmp, symbol)
```

指定されたシンボルのミューチュアルファンド保有者を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Mutual-Fund-Holders](https://site.financialmodelingprep.com/developer/docs/#Mutual-Fund-Holders)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL のミューチュアルファンド保有者を取得
data = mutual_fund_holders(fmp, "AAPL")
```
