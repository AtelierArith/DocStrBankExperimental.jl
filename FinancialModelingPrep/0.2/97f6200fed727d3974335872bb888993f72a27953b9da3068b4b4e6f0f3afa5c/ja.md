```
senate_trades(fmp, symbol)
```

指定されたシンボルの上院取引を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Senate-Trading](https://site.financialmodelingprep.com/developer/docs/#Senate-trading)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の上院取引を取得
data = senate_trades(fmp, "AAPL")
```
