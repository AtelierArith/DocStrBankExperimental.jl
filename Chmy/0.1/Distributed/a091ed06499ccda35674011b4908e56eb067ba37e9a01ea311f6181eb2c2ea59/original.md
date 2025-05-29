```
BoundaryConditions.bc!(side::Side, dim::Dim,
                            arch::DistributedArchitecture,
                            grid::StructuredGrid,
                            batch::ExchangeBatch)
```

Apply boundary conditions on a distributed grid with halo exchange performed internally.

# Arguments

  * `side`: The side of the grid where the halo exchange is performed.
  * `dim`: The dimension along which the halo exchange is performed.
  * `arch`: The distributed architecture used for communication.
  * `grid`: The structured grid on which the halo exchange is performed.
  * `batch`: The batch set to apply boundary conditions to.
