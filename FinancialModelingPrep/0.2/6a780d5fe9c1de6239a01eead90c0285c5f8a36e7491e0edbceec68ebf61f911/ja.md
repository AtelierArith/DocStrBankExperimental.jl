```
mutual_fund_portfolio(fmp, symbol, params...)
mutual_fund_portfolio(fmp, cik, params...)
```

指定されたミューチュアルファンドのポートフォリオを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `cik::String`: CIK。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Historical-Mutual-Fund-Holdings-Portfolio](https://site.financialmodelingprep.com/developer/docs/#historical-mutual-fund-holdings-portfolio)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2021年末の VTSAX のポートフォリオを取得
data = mutual_fund_portfolio(fmp, "VTSAX", date = "2021-12-31")

# 2021年末の VEXPX のポートフォリオを取得
data = mutual_fund_portfolio(fmp, cik = "0000034066", date = "2021-12-31")
```
