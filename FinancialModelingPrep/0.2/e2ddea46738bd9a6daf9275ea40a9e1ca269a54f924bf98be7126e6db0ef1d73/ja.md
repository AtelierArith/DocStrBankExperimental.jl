```
economic_calendar(fmp, params...)
```

経済カレンダーイベントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Economic-Calendar](https://site.financialmodelingprep.com/developer/docs/#Economic-Calendar)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2022年第1四半期の経済カレンダーイベントを取得
data = economic_calendar(fmp, from = "2022-01-01", to = "2022-03-31")
```
