```
pop(vec::StaticVector)
```

Return a new vector with the last item in `vec` removed.

# Examples

```jldoctest
julia> pop(@SVector[1,2,3])
2-element SVector{2, Int64} with indices SOneTo(2):
 1
 2
```
