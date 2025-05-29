```
cash_flow_statements(fmp, symbol, reported = false, params...)
```

指定されたシンボルのキャッシュフロー計算書を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `reported::Bool`: 報告されたまたは正規化された計算書を返します。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Cash-Flow-Statements](https://site.financialmodelingprep.com/developer/docs#Company-Financial-Statements)を参照してください。 詳細については、[Cash-Flow-Statements-As-Reported](https://site.financialmodelingprep.com/developer/docs#Company-Financial-Statements-As-Reported)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の過去 10 四半期の計算書を取得
data = cash_flow_statements(fmp, "AAPL", period = "quarter", limit = 10)

# AAPL の報告された過去 5 年間の計算書を取得
data = cash_flow_statements(fmp, "AAPL", reported = true, limit = 5)
```
