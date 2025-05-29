```julia
findclosestabove(needles, haystack)
```

Return the index of the nearest value of the indexable collection `haystack` that is greater than (i.e., "above") each value in `needles`. If no such values exist, returns `lastindex(haystack)+1`.

### Examples

```julia
julia> findclosestabove(3.5, 1:10)
4

julia> findclosestabove(3:4, 1:10)
2-element Vector{Int64}:
 4
 5
```
