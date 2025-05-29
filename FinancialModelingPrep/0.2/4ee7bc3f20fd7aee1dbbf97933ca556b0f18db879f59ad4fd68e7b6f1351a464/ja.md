```
historical_price_quote(fmp, symbol, frequency = TIME_FREQUENCIES.daily, params...)
```

指定されたシンボルと頻度の履歴価格引用を含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。
  * `frequency::String`: 時間枠。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Historical-Stock-Quote](https://site.financialmodelingprep.com/developer/docs/#Stock-Historical-Price)を参照してください。 詳細については、[Historical-Index-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-stock-index-prices)を参照してください。 詳細については、[Historical-Euronext-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-EuroNext-prices)を参照してください。 詳細については、[Historical-TSX-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-TSX-prices)を参照してください。 詳細については、[Historical-Cryptocurrencies-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-Cryptocurrencies-Price)を参照してください。 詳細については、[Historical-Forex-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-Forex-Price)を参照してください。 詳細については、[Historical-Commodities-Quote](https://site.financialmodelingprep.com/developer/docs/#Historical-commodities-prices)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの15分間の履歴価格引用を取得
data = historical_price_quote(fmp, "AAPL", frequency = TIME_FREQUENCIES.minutes15)

# BTCUSDの4時間の履歴価格引用を取得
data = historical_price_quote(fmp, "BTCUSD", frequency = TIME_FREQUENCIES.hours4)

# EURUSDのデイリー履歴価格引用の時系列を取得
data = historical_price_quote(fmp, "EURUSD", frequency = TIME_FREQUENCIES.daily, timeseries = 5)
```
