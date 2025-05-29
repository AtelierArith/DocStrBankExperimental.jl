```
ParallelUpdate()
```

Fully parallel initialization and update by using atomic operations to avoid race conditions when adding points into the same cell. This is not available for all cell list implementations.

See [`GridNeighborhoodSearch`](@ref) for usage information.
