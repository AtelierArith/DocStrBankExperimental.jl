```
technical_indicators(fmp, symbol, frequency = TIME_FREQUENCIES.daily, period = 200, type = "SMA")
```

指定されたシンボルと頻度の履歴価格引用を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `frequency::String`: 時間の頻度。
  * `period::Integer`: インジケーターの期間。
  * `type::String`: インジケーターのタイプ。

詳細については、[Daily-Indicators](https://site.financialmodelingprep.com/developer/docs/#Daily-Indicators)を参照してください。 詳細については、[Intraday-Indicators](https://site.financialmodelingprep.com/developer/docs/#Intraday-Indicators)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の日次 50 期間 SMA を取得
data = technical_indicators(fmp, "AAPL", period = 50)

# AAPL の 15 分 10 期間 WMA を取得
data = technical_indicators(fmp, "AAPL", TIME_FREQUENCIES.minutes15, period = 10, type = "wma")
```
