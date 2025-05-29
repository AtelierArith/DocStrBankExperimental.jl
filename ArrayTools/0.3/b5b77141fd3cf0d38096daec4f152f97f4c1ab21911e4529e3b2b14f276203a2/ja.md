```
same_standard_size(A, B...) -> size(A)
```

配列 `A`, `B` などがすべて標準インデックスを持ち、同じサイズであるかどうかをチェックし、そのサイズを返します。配列のサイズがすべて同一でない場合、`DimensionMismatch` 例外がスローされます。配列が非標準インデックス（つまり、インデックスが1から始まらない）を持つ場合、`ArgumentError` 例外がスローされます。

参照: [`standard_size`](@ref), [`has_standard_indexing`](@ref).
