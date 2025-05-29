```
senate_disclosures(fmp, symbol)
```

指定されたシンボルの上院開示を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Senate-Disclosure](https://site.financialmodelingprep.com/developer/docs/#Senate-disclosure)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の上院開示を取得
data = senate_disclosures(fmp, "AAPL")
```
