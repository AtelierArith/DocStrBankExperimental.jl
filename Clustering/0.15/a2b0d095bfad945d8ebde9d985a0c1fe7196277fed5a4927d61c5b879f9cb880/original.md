```
initseeds_by_costs!(iseeds::AbstractVector{Int}, alg::SeedingAlgorithm,
                    costs::AbstractMatrix) -> iseeds
```

Initialize `iseeds` with the indices of cluster seeds for the `costs` matrix using the `alg` seeding algorithm.

Here, `costs[i, j]` is the cost of assigning points $i$ and $j$ to the same cluster. One may, for example, use the squared Euclidean distance between the points as the cost.
