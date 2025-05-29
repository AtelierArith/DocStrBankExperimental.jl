```
insert(v::V, i::Integer, x) where V <: AbstractCapacityVector{T} -> V
```

Return the `AbstractCapacityVector` obtained from `v` by inserting `x` at position `i`. The position `i` must be between `1` and `length(v)+1`.

This is the non-mutating analog of `Base.insert!`.

See also [`duplicate`](@ref).
