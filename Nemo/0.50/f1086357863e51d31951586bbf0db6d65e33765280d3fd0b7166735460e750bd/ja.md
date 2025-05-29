```
eigenvalues_with_multiplicities(A::ComplexMatrix)
```

行列 `A` の固有値とその代数的重複度をタプルのベクトル `(ComplexFieldElem, Int)` として返します。各タプル `(z, k)` は、$A$ の `k` 個の固有値のクラスターに対応します。

この関数は実験的です。
