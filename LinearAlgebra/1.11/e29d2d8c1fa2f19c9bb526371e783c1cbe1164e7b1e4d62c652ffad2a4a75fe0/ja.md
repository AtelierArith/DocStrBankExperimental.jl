```
RowMaximum
```

残りの行の中で最大の絶対値を持つ要素がピボット要素として選ばれます。これは浮動小数点行列のLU因子分解のデフォルト戦略であり、時には「部分ピボッティング」アルゴリズムと呼ばれます。

行列の[要素型](@ref eltype)は、[`abs`](@ref)メソッドを許容し、その結果の型は[`<`](@ref)メソッドを許容しなければならないことに注意してください。
