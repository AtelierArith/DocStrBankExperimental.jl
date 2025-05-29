```
available_crytocurrencies(fmp)
```

APIで利用可能なすべての暗号通貨を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[Cryptocurrencies-List](https://site.financialmodelingprep.com/developer/docs/#Historical-Cryptocurrencies-Price)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 利用可能なすべての暗号通貨のリストを取得
data = available_crytocurrencies(fmp)
```
