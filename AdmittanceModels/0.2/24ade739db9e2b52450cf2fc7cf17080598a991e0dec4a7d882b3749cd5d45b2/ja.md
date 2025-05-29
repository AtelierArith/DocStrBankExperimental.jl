```
nullbasis(mat::AbstractMatrix{<:Number}; warn::Bool=true)
```

`mat`のヌル空間の基底を形成する列を持つ`SparseMatrixCSC`を返します。`mat`が`sparse_nullbasis`の条件を満たす場合、スパース行列が返されます。そうでない場合は警告が発せられ、`LinearAlgebra.nullspace`関数が使用されます。
