```
cik_from_symbol(fmp, symbol)
```

指定されたシンボルに一致するすべてのCIKを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[CIK-Mapper](https://site.financialmodelingprep.com/developer/docs/#Stock-Insider-Trading)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# AAPLのCIKを取得
data = cik_from_symbol(fmp, "AAPL")
```
