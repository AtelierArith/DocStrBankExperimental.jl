```
SemiParallelUpdate()
```

Loop over all cells in parallel to mark cells with points that now belong to a different cell. Then, move points of affected cells serially to avoid race conditions. This is available for all cell list implementations and is the default when [`ParallelUpdate`](@ref) is not available.

See [`GridNeighborhoodSearch`](@ref) for usage information.
