```
generate_sprinkling(manifold, boundary, count[; preset_atoms = [], rng = default_rng()]) -> Vector{Coordinates}
```

Sprinkle `count` spacetime atoms into `boundary` on `manifold`. The sprinkling density is proportional to the volume element of the manifold, $\sqrt{-g}$.

The returned coordinates are always sorted by the time coordinate, such that $x_i \preceq x_j$ can only be true if $i \leq j$. Several code optimizations in this package rely on this ordering.

If one or more coordinate points are passed via `preset_atoms`, they will always be present in the generated sprinkling. Additionally, the `rng` parameter can be specified if you want to use a custom random number generator (for instance for specifying seeds).
