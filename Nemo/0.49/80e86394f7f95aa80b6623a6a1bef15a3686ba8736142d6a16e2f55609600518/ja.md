```
eigenvalues_with_multiplicities(M::MatElem{T}) where T <: FieldElem
```

行列 `M` の固有値（`base_ring(M)` に存在する）と、それらの代数的重複度を (根, 重複度) のタプルのベクトルとして返します。
