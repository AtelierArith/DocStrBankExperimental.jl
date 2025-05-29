```
balance_sheet_statements(fmp, symbol, reported = false, params...)
```

指定されたシンボルのバランスシートステートメントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `reported::Bool`: 報告されたステートメントまたは正規化されたステートメントを返します。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Balance-Sheet-Statements](https://site.financialmodelingprep.com/developer/docs#Company-Financial-Statements)を参照してください。 詳細については、[Balance-Sheet-Statements-As-Reported](https://site.financialmodelingprep.com/developer/docs#Company-Financial-Statements-As-Reported)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の過去 10 四半期のステートメントを取得
data = balance_sheet_statements(fmp, "AAPL", period = "quarter", limit = 10)

# AAPL の報告された過去 5 年間のステートメントを取得
data = balance_sheet_statements(fmp, "AAPL", reported = true, limit = 5)
```
