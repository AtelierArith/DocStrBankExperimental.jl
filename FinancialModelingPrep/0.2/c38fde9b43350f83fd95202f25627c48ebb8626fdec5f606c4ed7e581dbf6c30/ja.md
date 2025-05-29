```
stock_grades(fmp, symbol, params...)
```

指定されたシンボルの株式グレードを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Stock-Grade](https://site.financialmodelingprep.com/developer/docs/#Stock-Grade)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の最後の 100 株式グレードを取得
data = stock_grades(fmp, "AAPL", limit = 100)
```
