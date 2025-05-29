```
available_symbols(fmp)
```

API内のすべての利用可能なシンボルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[Symbols-List](https://site.financialmodelingprep.com/developer/docs/#Symbols-List)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# すべての利用可能なシンボルのリストを取得
data = available_symbols(fmp)
```
