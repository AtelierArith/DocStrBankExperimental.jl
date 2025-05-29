```
historical_splits(fmp, symbol)
```

指定されたシンボルの歴史的な株式分割を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Historical-Stock-Splits](https://site.financialmodelingprep.com/developer/docs/#Historical-Stock-Splits)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の歴史的な分割を取得
data = historical_splits(fmp, "AAPL")
```
