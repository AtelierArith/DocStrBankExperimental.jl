```
price_targets_summary(fmp, symbol)
```

指定されたシンボルの価格目標の概要を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Price-Target-Summary](https://site.financialmodelingprep.com/developer/docs/#Price-target-Summary)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの価格目標の概要を取得
data = price_targets_summary(fmp, "AAPL")
```
