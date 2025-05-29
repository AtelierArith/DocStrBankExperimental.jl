```
aggregate_neighbors(g, aggr, m)
```

Given a graph `g`, edge features `m`, and an aggregation operator `aggr` (e.g `+, min, max, mean`), returns the new node features 

$$
\mathbf{x}_i = \square_{j \in \mathcal{N}(i)} \mathbf{m}_{j\to i}
$$

Neighborhood aggregation is the second step of [`propagate`](@ref),  where it comes after [`apply_edges`](@ref).
