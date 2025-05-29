```
institution_portfolio_summary(fmp, cik)
```

指定された機関のポートフォリオの概要を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `cik::String`: CIK。

詳細については、[Institutional-Holdings-Portfolio-Positions-Summary](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holdings-Portfolio-Positions-Summary)を参照してください。

# 例

```julia
# FMP APIのインスタンスを作成
fmp = FMP()

# バークシャー・ハサウェイのポートフォリオの概要を取得
data = institution_portfolio_summary(fmp, cik = "0001067983")
```
