```julia
findclosest(needles, haystack)
```

Return the index of the numerically closest value in the indexable collection `haystack` for each value in `needles`. If muliple values are equally close, the first one is used

### Examples

```julia
julia> findclosest(3.4, 1:10)
3

julia> findclosest(3:4, 1:10)
2-element Vector{Int64}:
 3
 4
```
