```
nonempty_intervals(t)
```

Return the indices of all intervals of the knot set `t` that are non-empty.

# Examples

```jldoctest
julia> nonempty_intervals(ArbitraryKnotSet(3, [0.0, 1, 1, 3, 4, 6], 1, 3))
4-element Array{Int64,1}:
 1
 3
 4
 5
```
