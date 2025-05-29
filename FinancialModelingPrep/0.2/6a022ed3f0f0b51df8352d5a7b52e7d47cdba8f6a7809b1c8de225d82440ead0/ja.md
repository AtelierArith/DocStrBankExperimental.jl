```
price_targets_by_analyst(fmp, name)
```

指定された名前から価格目標を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。
  * `name::String`: アナリストの名前。

詳細については、[Price-Target-by-Analyst-Name](https://site.financialmodelingprep.com/developer/docs/#Price-Target-By-Analyst-Name)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# Tim Andersonから価格目標を取得
data = price_targets_by_analyst(fmp, name = "Tim%20Anderson")
```
