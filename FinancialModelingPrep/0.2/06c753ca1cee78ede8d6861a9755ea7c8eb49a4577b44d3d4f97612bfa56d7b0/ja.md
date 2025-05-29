```
beneficial_ownership(fmp, symbol)
```

指定されたシンボルの有益所有権を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Individual-Beneficial-Ownership](https://site.financialmodelingprep.com/developer/docs/#Individual-Beneficial-Ownership)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の有益所有権を取得
data = beneficial_ownership(fmp, "AAPL")
```
