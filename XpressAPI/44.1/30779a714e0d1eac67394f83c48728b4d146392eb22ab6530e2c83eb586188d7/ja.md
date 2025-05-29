```
XPRSgetpivotorder(prob, pivotorder)::pivotorder
```

基本変数のピボット順序を返します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `pivotorder::Union{XPRSallocatable,AbstractVector{Int32}}`: ピボット順序が返される長さROWSの整数配列。この引数に`XPRS_ALLOC`を渡すことで、関数が適切なサイズの配列を自動的に割り当てることができます。

# 戻り値

  * `pivotorder::AbstractVector{Int32}`: ピボット順序が返される長さROWSの整数配列。

C APIの対応する関数[XPRSgetpivotorder](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSgetpivotorder.html)のドキュメントも参照してください。
