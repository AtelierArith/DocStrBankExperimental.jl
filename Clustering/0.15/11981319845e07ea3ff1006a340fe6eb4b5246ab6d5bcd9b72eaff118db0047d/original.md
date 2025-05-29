```
cutree(hclu::Hclust; [k], [h]) -> Vector{Int}
```

Cut the `hclu` dendrogram to produce clusters at the specified level of granularity.

Returns the cluster assignments vector $z$ ($z_i$ is the index of the cluster for the $i$-th data point).

# Arguments

  * `k::Integer` (optional) the number of desired clusters.
  * `h::Real` (optional) the height at which the tree is cut.

If both `k` and `h` are specified, it's guaranteed that the number of clusters is not less than `k` and their height is not above `h`.

See also: [`hclust`](@ref)
