```
historical_employee_counts(fmp, symbol)
```

指定されたシンボルの歴史的な従業員数を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Historical-Number-of-Employees](https://site.financialmodelingprep.com/developer/docs/#Historical-Number-of-Employees)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の歴史的な従業員数を取得
data = historical_employee_counts(fmp, "AAPL")
```
