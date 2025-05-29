```
available_countries(fmp)
```

APIで利用可能なすべての国のJSON配列を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[Stock-Screener](https://site.financialmodelingprep.com/developer/docs/#Stock-Screener)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 利用可能なすべての国のリストを取得
data = available_countries(fmp)
```
