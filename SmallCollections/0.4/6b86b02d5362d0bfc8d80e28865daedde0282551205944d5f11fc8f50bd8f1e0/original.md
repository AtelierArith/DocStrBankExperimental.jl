```
support(v::AbstractFixedVector) -> SmallBitSet
```

Return the `SmallBitSet` with the indices of the non-zero elements of `v`.

See also [`SmallBitSet`](@ref).

# Example

```jldoctest
julia> v = FixedVector{4,Int8}([1, 0, 0, 3]);

julia> support(v)
SmallBitSet{UInt64} with 2 elements:
  1
  4
```
