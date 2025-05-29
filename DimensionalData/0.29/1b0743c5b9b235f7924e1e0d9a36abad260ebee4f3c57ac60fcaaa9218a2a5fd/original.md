```
unmergedims(A::AbstractDimArray, original_dims) => AbstractDimArray
unmergedims(A::AbstractDimStack, original_dims) => AbstractDimStack
```

Return a new array or stack whose dimensions are restored to their original prior to calling [`mergedims(A, dim_pairs)`](@ref).
