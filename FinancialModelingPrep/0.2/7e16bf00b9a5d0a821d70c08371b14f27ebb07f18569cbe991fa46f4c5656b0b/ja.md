```
available_forex_pairs(fmp)
```

APIで利用可能なすべての外国為替ペアを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[Forex-Pairs-List](https://site.financialmodelingprep.com/developer/docs/#Forex-(FX))を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 利用可能なすべての外国為替ペアのリストを取得
data = available_forex_pairs(fmp)
```
