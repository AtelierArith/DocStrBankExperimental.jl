```
institution_search(fmp, name)
```

指定された機関名に一致するすべてのCIKを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `name::String`: 機関名。

詳細については、[Institutional-Holders-Search](https://site.financialmodelingprep.com/developer/docs/#Institutional-Holders-Search)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# バークシャー・ハサウェイのCIKを取得
data = institution_search(fmp, name = "Berkshire%20Hathaway%20Inc")
```
