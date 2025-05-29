```
shares_float(fmp)
shares_float(fmp, symbol)
```

1つまたはすべてのシンボルの浮動株統計を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル、または指定しない場合はすべてのシンボル。

詳細については、[Shares-Float](https://site.financialmodelingprep.com/developer/docs/#Shares-Float)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# すべてのシンボルの浮動株を取得
data = shares_float(fmp)

# AAPLの浮動株を取得
data = shares_float(fmp, "AAPL")
```
