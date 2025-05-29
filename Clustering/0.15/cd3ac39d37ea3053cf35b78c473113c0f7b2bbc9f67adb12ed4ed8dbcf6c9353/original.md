```
initseeds!(iseeds::AbstractVector{Int}, alg::SeedingAlgorithm,
           X::AbstractMatrix) -> iseeds
```

Initialize `iseeds` with the indices of cluster seeds for the `X` data matrix using the `alg` seeding algorithm.
