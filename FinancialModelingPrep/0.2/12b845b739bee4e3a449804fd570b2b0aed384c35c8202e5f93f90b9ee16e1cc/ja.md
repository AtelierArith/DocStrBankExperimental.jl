```
fmp_articles(fmp, params...)
```

FMP記事のJSONオブジェクトを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については[FMP-Articles](https://site.financialmodelingprep.com/developer/docs/#FMP-Articles)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# ページ0からサイズ5のFMP記事を取得
data = fmp_articles(fmp, page = 0, size = 5)
```
