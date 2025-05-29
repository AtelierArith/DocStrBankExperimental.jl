```
assignments(R::ClusteringResult) -> Vector{Int}
```

Get the vector of cluster indices for each point.

`assignments(R)[i]` is the index of the cluster to which the $i$-th point is assigned.
