```
institutions_list(fmp)
```

CIKによるすべての企業を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[Institutions-List](https://site.financialmodelingprep.com/developer/docs/#Form-13F)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# すべての機関を取得
data = institutions_list(fmp)
```
