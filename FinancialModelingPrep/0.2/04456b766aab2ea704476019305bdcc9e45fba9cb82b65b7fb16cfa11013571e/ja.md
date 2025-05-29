```
institutional_positions(fmp, symbol, params...)
```

指定されたシンボルの機関投資家のポジションを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。
  * `params...`: 追加のキーワードクエリパラメータ。

詳細については、[Institutional-Stock-Ownership](https://site.financialmodelingprep.com/developer/docs/#Institutional-Stock-Ownership)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# 現在の四半期を含む AAPL の機関投資家のポジションを取得
data = institutional_positions(fmp, "AAPL", includeCurrentQuarter = true)
```
