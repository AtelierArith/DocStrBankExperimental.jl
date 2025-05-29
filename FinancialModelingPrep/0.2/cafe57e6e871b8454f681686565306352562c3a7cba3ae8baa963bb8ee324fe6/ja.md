```
etf_country_weightings(fmp, symbol)
```

指定されたシンボルの国別ウェイトを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: ETF シンボル。

詳細については、[ETF-Country-Weightings](https://site.financialmodelingprep.com/developer/docs/#ETF-Country-Weightings)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# SPY の国別ウェイトを取得
data = etf_country_weightings(fmp, "SPY")
```
