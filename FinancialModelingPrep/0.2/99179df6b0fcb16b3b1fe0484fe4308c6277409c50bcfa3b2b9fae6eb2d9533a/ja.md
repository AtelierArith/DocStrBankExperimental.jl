```
financial_statements(fmp, symbol, params...)
```

指定されたシンボルに対して報告された財務諸表を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Full-Financial-Statements-As-Reported](https://site.financialmodelingprep.com/developer/docs#Company-Financial-Statements-As-Reported)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の報告されたすべての四半期財務諸表を取得
data = financial_statements(fmp, "AAPL", period = "quarter")
```
