```
tpod(red_style::ReductionStyle,A::AbstractMatrix) -> AbstractMatrix
tpod(red_style::ReductionStyle,A::AbstractMatrix,X::AbstractSparseMatrix) -> AbstractMatrix
```

行列 `A` の切り詰めた適切直交分解。提供される場合、`X` は出力が直交するようにするための（対称的で正定値の）ノルム行列です。`X` が提供されない場合、出力はユークリッドノルムに関して直交します。
