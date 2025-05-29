```
historical_discounted_cash_flows(fmp, symbol, params...)
```

指定されたシンボルの歴史的割引キャッシュフローを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Historical-Discounted-Cash-Flow](https://site.financialmodelingprep.com/developer/docs/#Company-Discounted-cash-flow-value)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 過去30四半期のAAPLのDCFを取得
data = historical_discounted_cash_flows(fmp, "AAPL", period = "quarter", limit = 30)
```
