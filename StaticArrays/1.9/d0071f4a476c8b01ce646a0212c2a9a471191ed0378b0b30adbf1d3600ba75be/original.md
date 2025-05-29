```
pushfirst(vec::StaticVector, item)
```

Return a new `StaticVector` with `item` inserted at the beginning of `vec`.

# Examples

```jldoctest
julia> pushfirst(@SVector[1, 2, 3, 4], 5)
5-element SVector{5, Int64} with indices SOneTo(5):
 5
 1
 2
 3
 4
```
