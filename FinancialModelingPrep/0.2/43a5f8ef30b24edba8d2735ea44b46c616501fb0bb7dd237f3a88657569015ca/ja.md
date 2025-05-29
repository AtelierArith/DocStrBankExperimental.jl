```
esg_ratings(fmp, symbol)
```

指定されたシンボルのESG評価を含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[ESG-Ratings](https://site.financialmodelingprep.com/developer/docs/#Company-ESG-Risk-Ratings)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLのESG評価を取得
data = esg_ratings(fmp, "AAPL")
```
