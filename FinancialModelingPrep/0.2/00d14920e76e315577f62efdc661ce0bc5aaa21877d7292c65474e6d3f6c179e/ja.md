```
crowdfunding_offerings_feed(fmp, params...)
```

RSSフィードからクラウドファンディングオファリングを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Crowdfunding-Offerings-Rss-Feed](https://site.financialmodelingprep.com/developer/docs/#Crowdfunding-Offerings-Rss-feed)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# RSSフィードから結果の最初のページを取得
data = crowdfunding_offerings_feed(fmp, page = 0)
```
