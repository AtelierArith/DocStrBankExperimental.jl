```
mergedims(A::AbstractDimArray, dim_pairs::Pair...) => AbstractDimArray
mergedims(A::AbstractDimStack, dim_pairs::Pair...) => AbstractDimStack
```

Return a new array or stack whose dimensions are the result of [`mergedims(dims(A), dim_pairs)`](@ref).
