```
intersection(Z::AbstractZonotope{N}, H::HalfSpace{N};
             [backend]=default_lp_solver(N), [prune]::Bool=true) where {N}
```

Compute the intersection between a zonotopic set and a half-space.

### Input

  * `Z`       – zonotopic set
  * `H`       – half-space
  * `backend` – (optional, default: `default_lp_solver(N)`) the LP solver used              for the removal of redundant constraints
  * `prune`   – (optional, default: `true`) flag for removing redundant              constraints

### Output

If the sets do not intersect, the output is the empty set. If the zonotopic set is fully contained in the half-space, the zonotopic set is returned. Otherwise, the output is the concrete intersection between `Z` and `H`.

### Algorithm

First there is a disjointness test. If that is negative, there is an inclusion test. If that is negative, then the concrete intersection is computed.
