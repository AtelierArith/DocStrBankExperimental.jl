```
SmallBitSet{U<:Unsigned} <: AbstractSet{Int}

SmallBitSet{U}([iter])
SmallBitSet([iter])
```

`SmallBitSet{U}` is an immutable set that can hold integers between `1` and the bit length of `U`. Called without an argument, it returns an empty set. If `U` is omitted, then `UInt` is taken.

All non-mutating functions for sets are supported. The non-mutating analogs [`push`](@ref push(::SmallBitSet, ::Vararg{Any})), [`pop`](@ref pop(::SmallBitSet)) and [`delete`](@ref) of the corresponding `!`-functions are also provided.
