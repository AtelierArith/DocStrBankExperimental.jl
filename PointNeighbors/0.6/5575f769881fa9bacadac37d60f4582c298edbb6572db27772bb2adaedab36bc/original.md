```
SerialIncrementalUpdate()
```

Deactivate parallelization in the neighborhood search update. Parallel neighborhood search update can be one of the largest sources of error variations between simulations with different thread numbers due to neighbor ordering changes. This strategy incrementally updates the cell lists in every update.

See [`GridNeighborhoodSearch`](@ref) for usage information.
