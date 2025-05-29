```
general_news(fmp, params...)
```

一般的なニュース記事を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[General-News](https://site.financialmodelingprep.com/developer/docs/#General-news)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 一般的なニュースの最初のページを取得
data = general_news(fmp, page = 0)
```
