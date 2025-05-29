```
analyst_estimates(fmp, symbol, params...)
```

指定されたシンボルのアナリスト予測を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Analyst-Estimates](https://site.financialmodelingprep.com/developer/docs/#Analyst-Estimates)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の過去 4 四半期のアナリスト予測を取得
data = analyst_estimates(fmp, "AAPL", period = "quarter", limit = 4)
```
