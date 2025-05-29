```
φnodes(grid::AbstractCurvilinearGrid, ℓx, ℓy, ℓz, with_halos=false)
```

Return the positions over the interior nodes on a curvilinear `grid` in the $φ$-direction for the location `ℓλ`, `ℓφ`, `ℓz`. For `Bounded` directions, `Face` nodes include the boundary points.

See [`znodes`](@ref) for examples.
