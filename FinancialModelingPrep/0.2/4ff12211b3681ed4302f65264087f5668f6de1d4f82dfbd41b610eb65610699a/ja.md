```
enterprise_values(fmp, symbol, params...)
```

指定されたシンボルの企業価値コンポーネントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Enterprise-Value](https://site.financialmodelingprep.com/developer/docs/#Company-Enterprise-Value)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 過去30四半期のAAPLの企業価値を取得
data = enterprise_values(fmp, "AAPL", period = "quarter", limit = 30)
```
