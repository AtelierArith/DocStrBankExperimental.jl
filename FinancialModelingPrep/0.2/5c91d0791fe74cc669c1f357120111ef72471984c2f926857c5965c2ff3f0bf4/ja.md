```
etf_portfolio_dates(fmp, symbol)
etf_portfolio_dates(fmp, cik)
```

指定されたETFのポートフォリオ日付を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。
  * `cik::String`: CIK。

詳細については、[Historical-Mutual-Fund-Holdings-Available-Dates](https://site.financialmodelingprep.com/developer/docs/#historical-mutual-fund-holdings-available-dates)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# VOOのポートフォリオ日付を取得
data = etf_portfolio_dates(fmp, "VOO")

# DLRのポートフォリオ日付を取得
data = etf_portfolio_dates(fmp, cik = "0000036405")
```
