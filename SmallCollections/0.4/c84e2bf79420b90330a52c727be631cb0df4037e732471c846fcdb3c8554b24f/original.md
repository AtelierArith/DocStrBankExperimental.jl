```
exchange(s::S, i::Integer, j::Integer) where S <: SmallBitSet -> S
```

Return the set `s` with the element `i`, if present, replaced by `j` and vice versa. If `i` equals `j`, then the set is not modified.

This function is faster than the equivalent `replace(s, i => j, j => i)`.

See also `Base.replace`.

# Examples

```jldoctest
julia> s = SmallBitSet((1, 2)); exchange(s, 1, 2)
SmallBitSet{UInt64} with 2 elements:
  1
  2

julia> s = SmallBitSet((1, 2)); exchange(s, 2, 3)
SmallBitSet{UInt64} with 2 elements:
  1
  3

julia> s = SmallBitSet((1, 2)); exchange(s, 3, 4)
SmallBitSet{UInt64} with 2 elements:
  1
  2

julia> s = SmallBitSet((1, 2)); exchange(s, 1, 1)
SmallBitSet{UInt64} with 2 elements:
  1
  2
```
