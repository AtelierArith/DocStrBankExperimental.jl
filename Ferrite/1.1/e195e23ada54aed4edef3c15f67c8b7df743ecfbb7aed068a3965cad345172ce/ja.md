```
allocate_matrix(::Type{Symmetric{Tv, SparseMatrixCSC{Tv, Ti}}}, sp::SparsityPattern)
```

`Symmetric{Tv, SparseMatrixCSC{Tv, Ti}}`型のスパース行列を、スパースパターン`sp`からインスタンス化します。結果として得られる行列は、対角線上およびそれ以上のエントリのみを格納します。
