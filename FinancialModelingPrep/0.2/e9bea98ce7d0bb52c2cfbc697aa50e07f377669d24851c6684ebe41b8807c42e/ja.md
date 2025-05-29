```
price_change(fmp, symbol)
```

指定されたシンボルの価格変動を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `symbol::String`: 株式シンボル。

詳細については、[Price-Change](https://site.financialmodelingprep.com/developer/docs/#Stock-price-change)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# AAPL の価格変動を取得
data = price_change(fmp, "AAPL")
```
