```
price_targets_feed(fmp, params...)
```

価格ターゲットフィードの結果を含むJSONテーブルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Price-Target-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#Price-Target-RSS-Feed)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 価格ターゲットフィードの最初のページを取得
data = price_targets_feed(fmp, page = 0)
```
