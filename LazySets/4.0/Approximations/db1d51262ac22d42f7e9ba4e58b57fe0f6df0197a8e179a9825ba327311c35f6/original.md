```
underapproximate(X::S, dirs::AbstractDirections;
                [apply_convex_hull]::Bool=false) where {N, S<:LazySet{N}}
```

Compute the underapproximation of a convex set by sampling support vectors.

### Input

  * `X`                 – convex set
  * `dirs`              – directions
  * `apply_convex_hull` – (optional, default: `false`) if `true`, post-process                        the support vectors with a convex hull operation

### Output

The `VPolytope` obtained by taking the convex hull of support vectors of `X` along the directions determined by `dirs`.

### Notes

Since the support vectors are not always unique, this algorithm may return a strict underapproximation even if the set can be exactly approximated using the given template.
