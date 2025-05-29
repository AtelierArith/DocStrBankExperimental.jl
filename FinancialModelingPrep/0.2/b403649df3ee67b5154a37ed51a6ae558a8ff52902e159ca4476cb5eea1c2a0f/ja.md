```
equity_offerings_feed(fmp, params...)
```

RSSフィードから株式オファリングを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Equity-Offerings-Fundraising-Rss-feed](https://site.financialmodelingprep.com/developer/docs/#Equity-offerings-Fundraising-Rss-feed)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# RSSフィードから結果の最初のページを取得
data = equity_offerings_feed(fmp, page = 0)
```
