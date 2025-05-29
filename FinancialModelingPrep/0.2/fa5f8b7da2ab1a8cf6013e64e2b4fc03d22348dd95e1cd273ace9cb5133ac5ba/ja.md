```
insider_trades_feed(fmp, params...)
```

RSSフィードからインサイダー取引を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については[Insider-Trading-RSS-Feed](https://site.financialmodelingprep.com/developer/docs/#Insider-Trading-RSS-Feed)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# フィードから最新のインサイダー取引を取得
data = insider_trades_feed(fmp, page = 0)
```
