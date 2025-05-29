```
duplicate(v::V, i::Integer, x) where V <: AbstractCapacityVector{T} -> V
```

Duplicate the `i`-th entry of `v` by inserting it at position `i+1` and return the new vector.

See also [`insert`](@ref).

# Example

```jldoctest
julia> v = SmallVector{8,Int8}(1:3)
3-element SmallVector{8, Int8}:
 1
 2
 3

julia> duplicate(v, 2)
4-element SmallVector{8, Int8}:
 1
 2
 2
 3
```
