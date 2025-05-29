```
matrix_phases_to_vec(M::AbstractMatrix{T}, phases::AbstractVector{Int}) where T
```

KVL制約を定義する際に使用されるこのメソッドは、ベクトル内の`phases`のインデックスにある`M`のエントリを返します。
