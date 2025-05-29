```julia
getFactorsAmongVariablesOnly(dfg, varlist; unused)

```

変数リストにある変数のみに依存する因子のリストを返します - すなわち、変数の中で。

## 注意事項

  * `unused::Bool=true` は、すでに使用されている因子を無視します - すなわち、`potentialused=true` の場合は無視します。
