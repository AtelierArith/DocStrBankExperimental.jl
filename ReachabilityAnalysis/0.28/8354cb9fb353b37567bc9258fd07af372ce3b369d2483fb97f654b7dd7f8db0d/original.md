```
convexify(fp::AbstractVector{<:AbstractLazyReachSet{N}}) where {N}
```

Return a reach-set representing the convex hull array of the array of the array of reach-sets.

### Input

  * `fp` – array of reach-sets

### Output

A reach-set that contains the convex hull array, `ConvexHullArray`, of the given flowpipe.

### Notes

The time span of this reach-set corresponds to the minimum (resp. maximum) of the time span of each reach-set in `fp`.

This function allocates an array to store the sets of the flowpipe.

The function doesn't assume that the reach-sets are time ordered.
