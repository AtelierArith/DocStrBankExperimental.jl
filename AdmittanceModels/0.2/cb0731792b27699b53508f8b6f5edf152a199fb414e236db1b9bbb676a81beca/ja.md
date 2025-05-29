```
sparse_nullbasis(mat::SparseMatrixCSC{<:Number, Int})
```

`mat`を次の特性を持つ行列とします

  * `mat`の任意の2行について、両方の行が非ゼロである列は最大1つです
  * `mat`の任意の列は最大2つの非ゼロ値を持ちます

`mat`のヌル空間の基底を形成する列を持つ疎行列を生成します。
