```
symbol_changes(fmp)
```

変更されたシンボルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prep インスタンス。

詳細については、[Symbol-Change](https://site.financialmodelingprep.com/developer/docs/#Symbol-Change)を参照してください。

# 例

```julia
# FMP API インスタンスを作成
fmp = FMP()

# シンボルの変更を取得
data = symbol_changes(fmp)
```
