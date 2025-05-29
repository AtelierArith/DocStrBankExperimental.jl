```
executive_compensation(fmp, symbol)
```

指定されたシンボルの役員報酬を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Executive-Compensation](https://site.financialmodelingprep.com/developer/docs/#Executive-Compensation)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の役員報酬を取得
data = executive_compensation(fmp, "AAPL")
```
