```
mutual_fund_search(fmp, name)
```

指定された名前に一致するすべての投資信託を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。
  * `name::String`: 機関名。

詳細については、[Mutual-Fund-Holdings-Search](https://site.financialmodelingprep.com/developer/docs/#Mutual-fund-holdings-search)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# バンガードのすべての投資信託を取得
data = mutual_fund_search(fmp, name = "Vanguard")
```
