```
push(vec::StaticVector, item)
```

Return a new `StaticVector` with `item` inserted on the end of `vec`.

# Examples

```jldoctest
julia> push(@SVector[1, 2, 3], 4)
4-element SVector{4, Int64} with indices SOneTo(4):
 1
 2
 3
 4
```
