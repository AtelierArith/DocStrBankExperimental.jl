```
institutional_holders(fmp, symbol)
```

指定されたシンボルの機関投資家を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Institutional-Holders](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holders)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の機関投資家を取得
data = institutional_holders(fmp, "AAPL")
```
