```
social_sentiment_trends(fmp, type, source)
```

指定されたシンボルのソーシャルセンチメントトレンドを含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `type::String:` "bullish"または"bearish"のいずれか。
  * `source::String:` "twitter"または"stocktwits"のいずれか。

詳細については、[Social-Sentiment](https://site.financialmodelingprep.com/developer/docs/#Social-Sentiment)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# すべてのソーシャルセンチメントトレンドを取得
data = social_sentiment_trends(fmp)

# ベアリッシュバイアスのあるstocktwitsからすべてのソーシャルセンチメントトレンドを取得
data = social_sentiment_trends(fmp, type = "bearish", source = "stocktwits")
```
