```
stock_split_calendar(fmp, params...)
```

株式分割カレンダーイベントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Stock-Split-Calendar](https://site.financialmodelingprep.com/developer/docs/#Stock-Split-Calendar)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2022年第1四半期の株式分割カレンダーイベントを取得
data = stock_split_calendar(fmp, from = "2022-01-01", to = "2022-03-31")
```
