```
institution_portfolio_composition(fmp, cik, params...)
```

指定された機関のポートフォリオ構成を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `cik::String`: CIK。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Institutional-Holdings-Portfolio-Composition](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holdings-Portfolio-composition)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 2021年第3四半期のバークシャー・ハサウェイのポートフォリオ構成を取得
data = institution_portfolio_composition(fmp, cik = "0001067983", date = "2021-09-30")
```
