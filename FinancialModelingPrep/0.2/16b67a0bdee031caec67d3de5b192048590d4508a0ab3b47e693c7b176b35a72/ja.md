```
crypto_news(fmp, params...)
```

暗号通貨ニュース記事を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Crypto-News](https://site.financialmodelingprep.com/developer/docs/#Crypto-news)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# BTCUSD のニュースの最初のページを取得
data = crypto_news(fmp, symbol = "BTCUSD", page = 0)
```
