```julia
findmatches(needles, haystack)
```

Return the linear index of the first value in `haystack` (if any) that is equal to a given value in `needles` for each value in `needles`; else 0.

### Examples

```julia
julia> findmatches([3,5],1:10)
2-element Vector{Int64}:
 3
 5
```
