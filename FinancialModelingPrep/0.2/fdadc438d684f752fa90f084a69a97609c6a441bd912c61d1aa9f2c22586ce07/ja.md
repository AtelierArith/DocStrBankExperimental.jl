```
stock_news_sentiment_feed(fmp, params...)
```

株式ニュース記事のセンチメントを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Stock-Sentiment](https://site.financialmodelingprep.com/developer/docs/#Stock-News)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 株式ニュース記事のセンチメントの最初のページを取得
data = stock_news_sentiment_feed(fmp, page = 0)
```
