```
sparse_matrix(A::MatElem; keepzrows::Bool = true)
```

密行列 $A$ に対応する疎行列を構築します。`keepzrows` が false の場合、コンストラクタは $A$ のゼロ行を削除します。
