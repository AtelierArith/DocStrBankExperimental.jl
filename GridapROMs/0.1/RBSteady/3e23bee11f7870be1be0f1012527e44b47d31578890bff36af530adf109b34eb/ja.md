```
gram_schmidt(A::AbstractMatrix,args...) -> AbstractMatrix
gram_schmidt(A::AbstractMatrix,X::AbstractSparseMatrix,args...) -> AbstractMatrix
```

行列 `A` に対するグラム・シュミット直交化をユークリッドノルムの下で行います。行列 `A` の行空間に対する内積を表す（正定値の）スパース行列 `X` を提供することで、異なるノルムの下で結果を直交させることができます。
