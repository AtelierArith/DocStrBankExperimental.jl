```
NamedArrayPartition(; kwargs...)
NamedArrayPartition(x::NamedTuple)
```

Similar to an `ArrayPartition` but the individual arrays can be accessed via the constructor-specified names. However, unlike `ArrayPartition`, each individual array must have the same element type.
