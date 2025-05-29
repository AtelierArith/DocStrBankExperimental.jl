```
senate_trades_feed(fmp, params...)
```

RSSフィードから上院の取引を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Senate-Trading-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#Senate-trading)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# RSSフィードから上院の取引の最初のページを取得
data = senate_trades_feed(fmp, page = 0)
```
