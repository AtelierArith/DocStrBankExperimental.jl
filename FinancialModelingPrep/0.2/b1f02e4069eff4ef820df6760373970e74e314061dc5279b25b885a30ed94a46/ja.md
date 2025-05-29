```
historical_social_sentiment(fmp, symbol, params...)
```

指定されたシンボルの歴史的なソーシャルセンチメントを含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Social-Sentiment](https://site.financialmodelingprep.com/developer/docs/#Social-Sentiment)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの歴史的なソーシャルセンチメントの最初のページを取得
data = historical_social_sentiment(fmp, "AAPL", page = 0)
```
