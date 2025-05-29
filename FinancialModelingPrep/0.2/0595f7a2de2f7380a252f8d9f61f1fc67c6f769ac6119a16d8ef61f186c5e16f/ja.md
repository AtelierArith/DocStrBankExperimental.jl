```
stock_peers(fmp, symbol)
```

指定されたシンボルの株のピアのJSON配列を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株のシンボル。

詳細については、[Stock-Peers](https://site.financialmodelingprep.com/developer/docs/#Stock-Peers)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLの株のピアを取得
data = stock_peers(fmp, "AAPL")
```
