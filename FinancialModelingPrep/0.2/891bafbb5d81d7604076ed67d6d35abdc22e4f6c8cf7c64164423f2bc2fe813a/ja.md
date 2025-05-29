```
stock_news(fmp, params...)
```

株式ニュース記事を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Stock-News](https://site.financialmodelingprep.com/developer/docs/#Stock-News)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL と FB の最新の株式ニュースを50件取得
data = stock_news(fmp, tickers = "AAPL,FB", limit = 50)
```
