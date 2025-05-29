```
overapproximate(CHA::ConvexHullArray{N, <:AbstractZonotope},
                ::Type{<:Zonotope}) where {N}
```

Overapproximate the convex hull of a list of zonotopic sets with a zonotope.

### Input

  * `CHA`      – convex hull array of zonotopic sets
  * `Zonotope` – target set type

### Output

A zonotope overapproximation of the convex hull array of zonotopic sets.

### Algorithm

This method iteratively applies the overapproximation algorithm to the convex hull of two zonotopic sets from the given array of zonotopic sets.
