```
discounted_cash_flows(fmp, symbol)
```

指定されたシンボルの割引キャッシュフローを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Discounted-Cash-Flow](https://site.financialmodelingprep.com/developer/docs/#Company-Discounted-cash-flow-value)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の DCF を取得
data = discounted_cash_flows(fmp, "AAPL")
```
