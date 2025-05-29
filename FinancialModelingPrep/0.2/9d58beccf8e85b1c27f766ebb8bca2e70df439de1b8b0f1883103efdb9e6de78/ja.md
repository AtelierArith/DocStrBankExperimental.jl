```
forex_news(fmp, params...)
```

外国為替ニュース記事を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Forex-News](https://site.financialmodelingprep.com/developer/docs/#Forex-news)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# EURUSD のニュースの最初のページを取得
data = forex_news(fmp, symbol = "EURUSD", page = 0)
```
