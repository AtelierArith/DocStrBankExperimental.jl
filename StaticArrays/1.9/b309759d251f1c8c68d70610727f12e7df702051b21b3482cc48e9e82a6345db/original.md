```
insert(vec::StaticVector, index::Integer, item)
```

Return a new vector with `item` inserted into `vec` at the given `index`.

# Examples

```jldoctest
julia> insert(@SVector[6, 5, 4, 2, 1], 4, 3)
6-element SVector{6, Int64} with indices SOneTo(6):
 6
 5
 4
 3
 2
 1
```
