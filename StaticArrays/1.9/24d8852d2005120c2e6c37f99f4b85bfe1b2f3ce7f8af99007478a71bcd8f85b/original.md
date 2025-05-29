```
deleteat(vec::StaticVector, index::Integer)
```

Return a new vector with the item at the given `index` removed.

# Examples

```jldoctest
julia> deleteat(@SVector[6, 5, 4, 3, 2, 1], 2)
5-element SVector{5, Int64} with indices SOneTo(5):
 6
 4
 3
 2
 1
```
