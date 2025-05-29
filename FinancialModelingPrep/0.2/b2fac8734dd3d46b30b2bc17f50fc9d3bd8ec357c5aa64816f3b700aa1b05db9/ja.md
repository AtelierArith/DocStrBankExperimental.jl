```
earnings_calendar_confirmed(fmp, params...)
```

確認された収益カレンダーイベントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Earnings-Calendar-Confirmed](https://site.financialmodelingprep.com/developer/docs/#Earnings-Calendar-Confirmed)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2022年第1四半期の確認された収益カレンダーイベントを取得
data = earnings_calendar_confirmed(fmp, from = "2022-01-01", to = "2022-03-31")
```
