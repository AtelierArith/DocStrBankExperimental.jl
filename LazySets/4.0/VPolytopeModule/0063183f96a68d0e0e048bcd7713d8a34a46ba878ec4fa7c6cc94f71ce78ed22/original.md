# Extended help

```
linear_map(M::AbstractMatrix, P::VPolytope; [apply_convex_hull]::Bool=false)
```

### Input

  * `apply_convex_hull` – (optional, default: `false`) flag for applying a convex                        hull to eliminate redundant vertices

### Algorithm

The linear map $M$ is applied to each vertex of the given set $P$, obtaining a polytope in vertex representation. The output type is again a `VPolytope`.
