```
ipo_calendar(fmp, params...)
```

IPOカレンダーイベントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については[IPO-Calendar](https://site.financialmodelingprep.com/developer/docs/#IPO-Calendar)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 2022年第1四半期のIPOカレンダーイベントを取得
data = ipo_calendar(fmp, from = "2022-01-01", to = "2022-03-31")
```
