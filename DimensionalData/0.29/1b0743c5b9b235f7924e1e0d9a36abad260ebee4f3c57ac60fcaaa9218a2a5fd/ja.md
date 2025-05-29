```
unmergedims(A::AbstractDimArray, original_dims) => AbstractDimArray
unmergedims(A::AbstractDimStack, original_dims) => AbstractDimStack
```

元の次元に戻された新しい配列またはスタックを返します。これは、[`mergedims(A, dim_pairs)`](@ref)を呼び出す前の状態です。
