```
popfirst(vec::StaticVector)
```

Return a new vector with the first item in `vec` removed.

# Examples

```jldoctest
julia> popfirst(@SVector[1,2,3])
2-element SVector{2, Int64} with indices SOneTo(2):
 2
 3
```
