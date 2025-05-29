```
etf_summary(fmp, symbol)
```

指定されたシンボルのETFサマリーを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[ETF-Info](https://site.financialmodelingprep.com/developer/docs/#ETF-Expense-ratio)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# SPYのETFサマリーを取得
data = etf_summary(fmp, "SPY")
```
