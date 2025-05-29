```
ynodes(grid, ℓx, ℓy, ℓz, with_halos=false)
```

Return the positions over the interior nodes on `grid` in the $y$-direction for the location `ℓx`, `ℓy`, `ℓz`. For `Bounded` directions, `Face` nodes include the boundary points.

See [`znodes`](@ref) for examples.
