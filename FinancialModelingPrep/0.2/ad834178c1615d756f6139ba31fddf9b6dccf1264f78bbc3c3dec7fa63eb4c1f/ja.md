```
etf_portfolio(fmp, symbol, params...)
etf_portfolio(fmp, cik, params...)
```

指定されたETFのポートフォリオを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。
  * `cik::String`: CIK。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Historical-Mutual-Fund-Holdings-Portfolio](https://site.financialmodelingprep.com/developer/docs/#historical-mutual-fund-holdings-portfolio)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 2021年末のVOOのポートフォリオを取得
data = etf_portfolio(fmp, "VOO", date = "2021-12-31")

# 2021年末のDLRのポートフォリオを取得
data = etf_portfolio(fmp, cik = "0000036405", date = "2021-12-31")
```
