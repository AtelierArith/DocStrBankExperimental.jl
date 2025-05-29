```
symbols_with_financials(fmp)
```

財務諸表を持つシンボルのJSON配列を返します。

# 引数

  * `fmp::FMP`: Financial Modeling Prepのインスタンス。

詳細については、[Financial-Statements-List](https://site.financialmodelingprep.com/developer/docs#Financial-Statements-List)を参照してください。

# 例

```julia
# FMP APIインスタンスを作成
fmp = FMP()

# 財務諸表を持つすべてのシンボルのリストを取得
data = symbols_with_financials(fmp)
```
