```
social_sentiment_changes(fmp, type, source)
```

指定されたシンボルのソーシャルセンチメントの変化を含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `type::String:` "bullish" または "bearish" のいずれか。
  * `source::String:` "twitter" または "stocktwits" のいずれか。

詳細については、[Social-Sentiment](https://site.financialmodelingprep.com/developer/docs/#Social-Sentiment)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# すべてのソーシャルセンチメントの変化を取得
data = social_sentiment_trends(fmp)

# bearishバイアスのあるstocktwitsからのすべてのソーシャルセンチメントの変化を取得
data = social_sentiment_changes(fmp, type = "bearish", source = "stocktwits")
```
