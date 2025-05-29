```
institution_portfolio_dates(fmp, cik)
```

指定された機関のポートフォリオ日付を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `cik::String`: CIK。

詳細については、[Institutional-Holders-Available-Date](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holders-Available-Date)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# バークシャー・ハサウェイのポートフォリオ日付を取得
data = institution_portfolio_dates(fmp, cik = "0001067983")
```
