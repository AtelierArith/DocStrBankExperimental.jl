```
key_executives(fmp, symbol)
```

指定されたシンボルの主要な役員を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Key-Executives](https://site.financialmodelingprep.com/developer/docs/#Key-Executives)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の主要な役員を取得
data = key_executives(fmp, "AAPL")
```
