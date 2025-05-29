```
available_tsx(fmp)
```

API内のすべての利用可能なtsxシンボルを返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[TSX-List](https://site.financialmodelingprep.com/developer/docs/#Most-of-the-TSX)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# すべての利用可能なtsxシンボルのリストを取得
data = available_tsx(fmp)
```
