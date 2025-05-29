```
vtall([p=identity,] A::AbstractArray, dims=:)
```

Determine whether predicate `p` returns true for all elements over the given `dims`. If `p` is omitted, test whether all values along the given `dims` are `true` (in which case `A` should be `AbstractArray{Bool}`). Threaded.

# Additional Notes

This function suffers from the same issue as `vfindmax` and friends – reductions which include the first dimension with max masks are not yet supported by LoopVectorization. Notably, this function still works as intended for any reduction which does not involve the first dimension.
