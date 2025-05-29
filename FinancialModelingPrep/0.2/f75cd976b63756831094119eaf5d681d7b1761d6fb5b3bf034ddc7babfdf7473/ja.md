```
price_targets(fmp, symbol)
```

指定されたシンボルの価格目標を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Price-Target](https://site.financialmodelingprep.com/developer/docs/#Price-Target)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の価格目標を取得
data = price_targets(fmp, "AAPL")
```
