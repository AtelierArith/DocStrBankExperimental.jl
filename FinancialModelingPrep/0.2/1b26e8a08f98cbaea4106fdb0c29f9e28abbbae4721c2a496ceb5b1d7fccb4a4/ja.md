```
company_information(fmp, symbol)
```

指定されたシンボルの会社情報を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Stock-Peers](https://site.financialmodelingprep.com/developer/docs/#Stock-Peers)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の会社情報を取得
data = company_information(fmp, "AAPL")
```
