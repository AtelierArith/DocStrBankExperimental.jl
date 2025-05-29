```
financial_reports(fmp, symbol, year, period = "FY")
```

指定されたシンボル、年、期間の財務報告のJSON辞書を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。
  * `year::Integer`: カレンダー年。
  * `period::String`: "FY"、"Q1"、"Q2"、"Q3"、または "Q4" のいずれか。

詳細については、[Annual-Reports-on-Form-10-K](https://site.financialmodelingprep.com/developer/docs#Annual-Reports-on-Form-10-K)を参照してください。 詳細については、[Quarterly-Earnings-Reports](https://site.financialmodelingprep.com/developer/docs/#Quarterly-Earnings-Reports)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 2022年のAAPLの10-Kを取得
data = financial_reports(fmp, "AAPL", year = 2022)

# 2022年Q4のAAPLの10-Qを取得
data = financial_reports(fmp, "AAPL", 2022, period = "Q4")
```
