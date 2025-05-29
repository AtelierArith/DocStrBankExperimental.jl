```
etf_exposure(fmp, symbol)
```

指定されたシンボルのETFエクスポージャーを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[ETF-Stock-Exposure](https://site.financialmodelingprep.com/developer/docs/#ETF-Stock-Exposure)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLのETFエクスポージャーを取得
data = etf_exposure(fmp, "AAPL")
```
