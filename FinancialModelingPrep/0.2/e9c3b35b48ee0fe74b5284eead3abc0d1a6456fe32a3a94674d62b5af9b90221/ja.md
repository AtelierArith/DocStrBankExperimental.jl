```
balance_sheet_statements_growth(fmp, symbol, params...)
```

指定されたシンボルのバランスシートの成長を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Balance-Sheet-Statements-Growth](https://site.financialmodelingprep.com/developer/docs/#Financial-Statements-Growth)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの過去5年間の成長を取得
data = balance_sheet_statements_growth(fmp, "AAPL", limit = 5)
```
