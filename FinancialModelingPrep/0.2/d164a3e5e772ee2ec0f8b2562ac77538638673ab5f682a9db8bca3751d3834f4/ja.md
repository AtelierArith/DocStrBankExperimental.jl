```
institutional_ownership_weightings(fmp, symbol, params...)
```

指定されたシンボルの機関投資家の所有割合を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Institutional-Stock-by-Shares-Held-and-Date](https://site.financialmodelingprep.com/developer/docs/#Institutional-Ownership-by-Shares-Held-and-Date)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2021年第3四半期のAAPLの機関投資家の所有割合を取得
data = institutional_ownership_weightings(fmp, "AAPL", date = "2021-09-30")
```
