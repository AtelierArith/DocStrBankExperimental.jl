```
treasury_rates(fmp, params...)
```

指定された日付範囲の国債利率を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Treasury-Rates](https://site.financialmodelingprep.com/developer/docs/#Treasury-Rates)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2022年第1四半期の国債利率を取得
data = treasury_rates(fmp, from = "2022-01-01", to = "2022-03-31")
```
