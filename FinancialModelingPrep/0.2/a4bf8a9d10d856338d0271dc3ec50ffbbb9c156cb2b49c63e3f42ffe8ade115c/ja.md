```
ipo_calendar_prospectus(fmp, params...)
```

プロスペクタスを持つIPOカレンダーイベントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[IPO-Calendar-with-Prospectus](https://site.financialmodelingprep.com/developer/docs/#IPO-calendar-with-prospectus)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 2022年第1四半期のプロスペクタスを持つIPOカレンダーイベントを取得
data = ipo_calendar_prospectus(fmp, from = "2022-01-01", to = "2022-03-31")
```
