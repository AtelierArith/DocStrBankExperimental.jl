```
tradeable_symbols(fmp)
```

API内のすべての取引可能なシンボルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[Tradeable-Symbols-List](https://site.financialmodelingprep.com/developer/docs/#Tradable-Symbols-List)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 利用可能なすべてのシンボルのリストを取得
data = tradeable_symbols(fmp)
```
