```
path_cost(f::Function, ::AbstractSparseMatrixCSC, r, n)
```

r[1:n]のパスの合計重みを返し、合計の前に各重みに`f`を適用します。
