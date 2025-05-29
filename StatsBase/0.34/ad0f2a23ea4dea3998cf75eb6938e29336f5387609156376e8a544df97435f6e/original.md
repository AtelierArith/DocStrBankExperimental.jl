```
rle(v) -> (vals, lens)
```

Return the run-length encoding of a vector as a tuple. The first element of the tuple is a vector of values of the input and the second is the number of consecutive occurrences of each element.

# Examples

```jldoctest
julia> using StatsBase

julia> rle([1,1,1,2,2,3,3,3,3,2,2,2])
([1, 2, 3, 2], [3, 2, 4, 3])
```
