```
convexify(fp::Flowpipe{N, <:AbstractLazyReachSet}) where {N}
```

Return a reach-set representing the convex hull array of the flowpipe.

### Input

  * `fp` – flowpipe

### Output

A reach-set that contains the convex hull array, `ConvexHullArray`, of the given flowpipe.

### Notes

The time span of this reach-set is the same as the time-span of the flowpipe.

This function allocates an array to store the sets of the flowpipe.
