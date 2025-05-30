```
searchsortedlast(v, x; by=identity, lt=isless, rev=false)
```

Return the index of the last value in `v` less than or equivalent to `x`. If `x` is less than all values in `v` the function returns `firstindex(v) - 1`.

The vector `v` must be sorted according to the order defined by the keywords. Refer to [`sort!`](@ref) for the meaning of the keywords and the definition of "less than" and equivalence. Note that the `by` function is applied to the searched value `x` as well as the values in `v`.

The index is generally found using binary search, but there are optimized implementations for some inputs

# Examples

```jldoctest
julia> searchsortedlast([1, 2, 4, 5, 5, 7], 4) # single match
3

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 5) # multiple matches
5

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 3) # no match, insert in the middle
2

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 9) # no match, insert at end
6

julia> searchsortedlast([1, 2, 4, 5, 5, 7], 0) # no match, insert at start
0

julia> searchsortedlast([1=>"one", 2=>"two", 4=>"four"], 3=>"three", by=first) # compare the keys of the pairs
2
```
