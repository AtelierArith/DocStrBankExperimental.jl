```
mutual_fund_portfolio_dates(fmp, symbol)
mutual_fund_portfolio_dates(fmp, cik)
```

指定されたミューチュアルファンドのポートフォリオ日付を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `cik::String`: CIK。

詳細については、[Historical-Mutual-Fund-Holdings-Available-Dates](https://site.financialmodelingprep.com/developer/docs/#historical-mutual-fund-holdings-available-dates)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# VTSAX のポートフォリオ日付を取得
data = mutual_fund_portfolio_dates(fmp, "VTSAX")

# VEXPX のポートフォリオ日付を取得
data = mutual_fund_portfolio_dates(fmp, cik = "0000034066")
```
