```
sparse_multiply(A::SparseMatrix, B::SparseMatrix)
```

2つのスパース行列を掛け算します。

行列の積が定義されていない場合や、エントリの型が一致しない場合は例外が発生します。
