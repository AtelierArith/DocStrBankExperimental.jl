```
fails_to_deliver(fmp, symbol, params)
```

指定されたシンボルの配達失敗を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Fails-to-Deliver](https://site.financialmodelingprep.com/developer/docs/#Fail-to-deliver)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の配達失敗の最初のページを取得
data = fails_to_deliver(fmp, "AAPL", page = 0)
```
