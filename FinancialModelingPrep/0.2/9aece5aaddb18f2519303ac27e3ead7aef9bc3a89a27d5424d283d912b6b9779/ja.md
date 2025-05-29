```
esg_scores(fmp, symbol)
```

指定されたシンボルのESGスコアを含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。

詳細については[ESG-Score](https://site.financialmodelingprep.com/developer/docs/#ESG-SCORE)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLのESGスコアを取得
data = esg_scores(fmp, "AAPL")
```
