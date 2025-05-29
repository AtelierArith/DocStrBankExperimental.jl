```
mergers_and_acquisitions_feed(fmp, params...)
```

マージと買収フィードの結果を含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Mergers-and-Acquisitions-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#MERGER-AND-ACQUISITION)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# マージと買収のRSSフィードの最初のページを取得
data = mergers_and_acquisitions_feed(fmp, page = 0)
```
