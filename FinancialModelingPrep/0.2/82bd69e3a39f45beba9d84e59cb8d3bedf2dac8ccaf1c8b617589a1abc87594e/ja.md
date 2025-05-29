```
exchange_rates(fmp)
exchange_rates(fmp, symbol)
```

指定されたシンボルのコモディティクォートを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: コモディティシンボル。

詳細については、[Crypto-Quote](https://site.financialmodelingprep.com/developer/docs/#Cryptocurrencies)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# すべての為替レートを取得
data = commodity_quote(fmp)

# EURUSD の為替レートを取得
data = commodity_quote(fmp, "EURUSD")
```
