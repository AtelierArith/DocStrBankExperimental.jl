```
etf_holders(fmp, symbol)
```

指定されたシンボルのETFホルダーを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: ETFシンボル。

詳細については、[ETF-Holders](https://site.financialmodelingprep.com/developer/docs/#ETF-Holders)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# SPYのETFホルダーを取得
data = etf_holders(fmp, "SPY")
```
