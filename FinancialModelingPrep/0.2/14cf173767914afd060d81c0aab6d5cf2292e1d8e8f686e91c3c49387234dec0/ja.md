```
available_euronext(fmp)
```

API内のすべての利用可能なユーロネクストシンボルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[Euronext-List](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-EuroNext)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 利用可能なすべてのユーロネクストシンボルのリストを取得
data = available_euronext(fmp)
```
