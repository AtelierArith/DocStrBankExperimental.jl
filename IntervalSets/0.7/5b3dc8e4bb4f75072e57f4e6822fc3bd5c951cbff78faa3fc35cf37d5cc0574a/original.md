```
searchsorted_interval(a, i::Interval; [rev=false])
```

Return the range of indices of `a` which is inside of the interval `i` (using binary search), assuming that `a` is already sorted. Return an empty range located at the insertion point if a does not contain values in `i`.

# Examples

```jldoctest
julia> searchsorted_interval([1,2,3,5], 2..4)
2:3

julia> searchsorted_interval([1,2,3,5], 4..1)
4:3

julia> searchsorted_interval(Float64[], 1..3)
1:0
```
