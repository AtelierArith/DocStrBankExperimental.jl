```
mergedims(A::AbstractDimArray, dim_pairs::Pair...) => AbstractDimArray
mergedims(A::AbstractDimStack, dim_pairs::Pair...) => AbstractDimStack
```

新しい配列またはスタックを返します。その次元は[`mergedims(dims(A), dim_pairs)`](@ref)の結果です。
