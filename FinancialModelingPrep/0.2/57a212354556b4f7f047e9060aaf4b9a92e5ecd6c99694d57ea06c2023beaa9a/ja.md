```
available_commodities(fmp)
```

APIで利用可能なすべてのコモディティを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については[Commodities-List](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-Major-Commodities-(Gold,-Silver,-Oil))を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 利用可能なすべてのコモディティのリストを取得
data = available_commodities(fmp)
```
