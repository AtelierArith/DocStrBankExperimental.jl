```
LittleSet([itr]) <: AbstractSet
```

Constructs an ordered set optimized for a small number of elements, given the iterable `itr`. The underlying data is stored as either an `AbstractVector` or a `Tuple` and is optimal for 30-50 elements, similar to [`LittleDict`](@ref).
