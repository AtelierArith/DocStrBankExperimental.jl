```
bisect_right(a, x, lo = 1, hi = length(a) + 1)
```

Return the index where to insert item `x` in array `a`, assuming `a` is in an non-decreasing order.

The return value `i` is such that all `e` in `a[:(i - 1)]` have `e <= x`, and all `e` in `a[i:]` have `e > x`.  So if `x` already appears in the array, `insert!(a, i, x)` will insert just after the rightmost `x` already there.

# Arguments

Optional args `lo` (default `1`) and `hi` (default `length(a) + 1`) bound the slice of `a` to be searched.

# Examples

```jldoctest
julia> bisect_right([1, 2, 3, 4, 5], 3.5)
4

julia> bisect_right([1, 2, 3, 4, 5], 2)
3

julia> bisect_right([1, 2, 3, 3, 3, 5], 3)
6
```
