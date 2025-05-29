```
etf_symbols(fmp)
```

API内のすべての取引可能なシンボルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[ETF-Symbols](https://site.financialmodelingprep.com/developer/docs/#ETF-List)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# すべてのETFシンボルのリストを取得
data = etf_symbols(fmp)
```
