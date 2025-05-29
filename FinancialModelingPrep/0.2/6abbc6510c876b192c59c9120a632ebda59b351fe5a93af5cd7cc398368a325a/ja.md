```
institutional_ownership_percentages(fmp, symbol, params...)
```

指定されたシンボルの機関投資家の保有割合を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Stock-Ownership-by-Holders](https://site.financialmodelingprep.com/developer/docs/#Stock-Ownership-by-Holders)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2021年第3四半期のAAPLの機関投資家の保有割合を取得
data = institutional_ownership_percentages(fmp, "AAPL", date = "2021-09-30")
```
