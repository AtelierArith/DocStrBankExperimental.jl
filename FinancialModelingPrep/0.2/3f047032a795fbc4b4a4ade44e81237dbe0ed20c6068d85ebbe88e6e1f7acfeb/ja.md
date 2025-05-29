```
institutional_ownership_feed(fmp, params...)
```

RSSフィードから機関投資家の所有権を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Institutional-Holder-Rss-Feed](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holder-Rss-Feed)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# RSSフィードから結果の最初のページを取得
data = institutional_ownership_feed(fmp, page = 0)
```
