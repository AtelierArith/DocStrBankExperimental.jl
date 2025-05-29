```
upgrades_and_downgrades_feed(fmp, params...)
```

RSSフィードからアップグレードとダウングレードを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Upgrades-&-Downgrades-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#Upgrades-&-Downgrades-RSS-Feed)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# アップグレードとダウングレードの最初のページを取得
data = upgrades_and_downgrades_feed(fmp, page = 0)
```
