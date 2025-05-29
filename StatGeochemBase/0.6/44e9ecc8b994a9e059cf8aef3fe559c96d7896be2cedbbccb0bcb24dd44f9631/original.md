```julia
findclosestbelow(needles, haystack)
```

Return the index of the nearest value of the indexable collection `haystack` that is less than (i.e., "below") each value in `needles`. If no such haystack values exist, returns `firstindex(haystack)-1`.

### Examples

```julia
julia> findclosestbelow(3.5, 1:10)
3

julia> findclosestbelow(3:4, 1:10)
2-element Vector{Int64}:
 2
 3    
```
