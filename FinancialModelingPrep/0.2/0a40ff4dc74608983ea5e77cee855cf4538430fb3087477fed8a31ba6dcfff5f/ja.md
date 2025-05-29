```
historical_ratings(fmp, symbol, params...)
```

指定されたシンボルの履歴評価を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Historical-Ratings](https://site.financialmodelingprep.com/developer/docs/#Company-Rating)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の最後の 100 件の評価を取得
data = historical_ratings(fmp, "AAPL", limit = 100)
```
