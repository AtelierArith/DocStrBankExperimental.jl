```
integrate(u::GridData,g::PhysicalGrid)
```

Calculate the discrete integral of grid data `u`, using the  cell volumes of grid `g`. If `u` is `VectorData`, then this returns a vector  of the integrals in each coordinate direction.
