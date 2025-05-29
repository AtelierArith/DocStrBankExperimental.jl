```
cik_search(fmp, name)
```

指定された名前に一致するすべてのCIKを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `name::String`: 完全または部分的な機関名。

詳細については、[Form-13F-Search](https://site.financialmodelingprep.com/developer/docs/#Form-13F)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# "Berkshire"に一致するすべてのCIKを取得
data = cik_search(fmp, name = "Berkshire")
```
