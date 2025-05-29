# Extended help

```
vertices_list(Z::AbstractZonotope; [apply_convex_hull]::Bool=true)
```

### Input

  * `apply_convex_hull` – (optional, default: `true`) if `true`, post-process the                        computation with the convex hull of the points

### Algorithm

#### Two-dimensional case

We use a trick to speed up enumerating vertices of 2-dimensional zonotopic sets with all generators in the first quadrant or third quadrant (same sign). Namely, sort the generators by angle and add them clockwise in increasing order and counterclockwise in decreasing order. A more detailed explanation can be found [here](https://math.stackexchange.com/q/3356460).

To avoid the cumulative sum from both directions separately, we build a 2D index matrix to sum generators for both directions in one matrix-vector product.

#### General case

If the zonotopic set has $p$ generators, each vertex is the result of summing the center with some linear combination of generators, where the combination factors are $ξ_i ∈ \{-1, 1\}$.

There are at most $2^p$ distinct vertices. Use the flag `apply_convex_hull` to control whether a convex-hull algorithm is applied to the vertices computed by this method; otherwise, redundant vertices may be present.
