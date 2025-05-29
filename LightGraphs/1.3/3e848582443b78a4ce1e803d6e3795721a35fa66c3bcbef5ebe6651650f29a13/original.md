```
weights(g)
```

Return the weights of the edges of a graph `g` as a matrix. Defaults to [`LightGraphs.DefaultDistance`](@ref).

### Implementation Notes

In general, referencing the weight of a nonexistent edge is undefined behavior. Do not rely on the `weights` matrix as a substitute for the graph's [`adjacency_matrix`](@ref).
