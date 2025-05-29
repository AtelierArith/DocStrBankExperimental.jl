```
historical_dividends(fmp, symbol)
```

指定されたシンボルの履歴配当のJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Historical-Dividends](https://site.financialmodelingprep.com/developer/docs/#Historical-Dividends)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの最後の履歴配当を取得
data = historical_dividends(fmp, "AAPL")
```
