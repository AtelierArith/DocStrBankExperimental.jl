```
initseeds_by_costs(alg::Union{SeedingAlgorithm, Symbol},
                   costs::AbstractMatrix, k::Integer) -> Vector{Int}
```

Select `k` seeds from the $n×n$ `costs` matrix using algorithm `alg`.

Here, `costs[i, j]` is the cost of assigning points `i``and``j`` to the same cluster. One may, for example, use the squared Euclidean distance between the points as the cost.

Returns the vector of `k` seed indices.
