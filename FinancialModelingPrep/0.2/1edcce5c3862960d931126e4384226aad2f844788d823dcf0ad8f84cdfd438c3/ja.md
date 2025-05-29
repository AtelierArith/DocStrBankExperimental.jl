```
available_indexes(fmp)
```

すべての利用可能なインデックスを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。

詳細については、[Available-Indexes](https://site.financialmodelingprep.com/developer/docs/#Historical-stock-index-prices)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# すべての利用可能なインデックスのリストを取得
data = available_indexes(fmp)
```
