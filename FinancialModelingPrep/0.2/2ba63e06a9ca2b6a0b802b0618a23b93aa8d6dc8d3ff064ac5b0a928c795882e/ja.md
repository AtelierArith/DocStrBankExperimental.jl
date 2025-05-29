```
revenue_segments(fmp, symbol, segment = REVENUE_SEGMENTS.product, params...)
```

指定されたシンボルの収益セグメントを含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。
  * `segment::String`: `REVENUE_SEGMENTS`オプション。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Sales-Revenue-By-Segments](https://site.financialmodelingprep.com/developer/docs/#Sales-Revenue-By-Segments)を参照してください。 詳細については、[Revenue-Geographic-by-Segments](https://site.financialmodelingprep.com/developer/docs/#Revenue-Geographic-by-Segments)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLのすべての年次地理的収益セグメントを取得
data = revenue_segments(fmp, "AAPL", segment = REVENUE_SEGMENTS.geographic, structure = "flat")

# AAPLのすべての四半期製品収益セグメントを取得
data = revenue_segments(fmp, "AAPL", segment = REVENUE_SEGMENTS.product, period = "quarter", structure = "flat")
```
