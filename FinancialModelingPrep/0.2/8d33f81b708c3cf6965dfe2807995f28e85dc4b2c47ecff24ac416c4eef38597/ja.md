```
dividend_calendar(fmp, params...)
```

配当カレンダーイベントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Dividend-Calendar](https://site.financialmodelingprep.com/developer/docs/#Dividend-Calendar)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2022年第1四半期の配当カレンダーイベントを取得
data = dividend_calendar(fmp, from = "2022-01-01", to = "2022-03-31")
```
