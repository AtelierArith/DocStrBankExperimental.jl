```
bc!(arch::Architecture, grid::StructuredGrid, batch::BatchSet)
```

Apply boundary conditions using a batch set `batch` containing an `AbstractBatch` per dimension per side of `grid`.

# Arguments

  * `arch`: The architecture.
  * `grid`: The grid.
  * `batch:`: The batch set to apply boundary conditions to.
