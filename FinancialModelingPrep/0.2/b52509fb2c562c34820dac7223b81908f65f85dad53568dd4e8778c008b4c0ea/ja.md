```
ipo_calendar_confirmed(fmp, params...)
```

確認されたIPOカレンダーイベントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[IPO-Calendar-Confirmed](https://site.financialmodelingprep.com/developer/docs/#IPO-calendar-Confirmed)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 2022年第1四半期の確認されたIPOカレンダーイベントを取得
data = ipo_calendar_confirmed(fmp, from = "2022-01-01", to = "2022-03-31")
```
