```
advanced_discounted_cash_flows(fmp, symbol, levered = false)
```

指定されたシンボルの高度な割引キャッシュフローを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `levered::Bool`: WACCを含むレバレッジ付きDCFを返します。

詳細については、[Discounted-Cash-Flow](https://site.financialmodelingprep.com/developer/docs/#Company-Discounted-cash-flow-value)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の WACC を含むレバレッジ付きDCFを取得
data = advanced_discounted_cash_flows(fmp, "AAPL", levered = true)
```
