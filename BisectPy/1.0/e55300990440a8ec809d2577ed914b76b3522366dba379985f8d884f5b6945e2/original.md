```
insort_right(a, x, lo = 1, hi = nothing)
```

Insert item `x` in array `a`, and keep it sorted assuming `a` is sorted.

If `x` is already in `a`, insert it to the right of the rightmost `x`. Optional args `lo` (default `1`) and `hi` (default `length(a)`) bound the slice of `a` to be searched.
