```
support(v::AbstractCapacityVector) -> SmallBitSet
```

Return the `SmallBitSet` with the indices of the non-zero elements of `v`.

See also [`SmallBitSet`](@ref).

# Example

```jldoctest
julia> v = SmallVector{8,Int8}([1, 0, 2, 0, 0, 3]);

julia> support(v)
SmallBitSet{UInt64} with 3 elements:
  1
  3
  6
```
