```
company_notes(fmp, symbol)
```

指定されたシンボルのためのノートを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Company-Notes-Due](https://site.financialmodelingprep.com/developer/docs/#Company-Notes-due)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL のすべてのノートを取得
data = company_notes(fmp, "AAPL")
```
