```
DiagOp(ops...)
DiagOp(ops::Vector{...})
DiagOp(ops::NTuple{N,...})
```

`ops` に含まれる `LinearOperator` または `Array` からブロック対角演算子を作成します。
