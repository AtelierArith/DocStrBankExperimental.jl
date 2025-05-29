```
economic_indicator(fmp, name, params...)
```

指定された日付範囲の国債利率を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `name::String`: 経済指標。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Economic-Indicator](https://site.financialmodelingprep.com/developer/docs/#Economic-Indicator)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2022年第1四半期の実質GDPを取得
data = economic_indicator(fmp, name = "realGDP", from = "2022-01-01", to = "2022-03-31")

# 2022年第1四半期のフェデラルファンド金利を取得
data = economic_indicator(fmp, name = "federalFunds", from = "2022-01-01", to = "2022-03-31")
```
