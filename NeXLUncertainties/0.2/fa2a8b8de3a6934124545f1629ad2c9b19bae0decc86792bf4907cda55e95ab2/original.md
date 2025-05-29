```
labelsByType(ty::Type{<:Label}, labels::AbstractVector{<:Label})
labelsByType(types::AbstractVector{DataType}, labels::AbstractVector{<:Label})
```

Extracts all of a specific type of `Label` from a list of `Label`s. The second version extracts multiple different types in a single call.
