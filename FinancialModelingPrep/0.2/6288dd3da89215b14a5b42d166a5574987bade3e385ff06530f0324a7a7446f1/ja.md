```
etf_sector_weightings(fmp, symbol)
```

指定されたシンボルのセクターウェイトを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: ETFシンボル。

詳細については、[ETF-Sector-Weightings](https://site.financialmodelingprep.com/developer/docs/#ETF-Sector-Weightings)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# SPYのセクターウェイトを取得
data = etf_sector_weightings(fmp, "SPY")
```
