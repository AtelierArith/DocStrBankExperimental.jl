```
historical_earnings_calendar(fmp, symbol, params...)
```

過去の収益カレンダーイベントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Earnings-Calendar](https://site.financialmodelingprep.com/developer/docs/#Earnings-Calendar)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの過去50件の収益カレンダーイベントを取得
data = historical_earnings_calendar(fmp, "AAPL", limit = 50)
```
