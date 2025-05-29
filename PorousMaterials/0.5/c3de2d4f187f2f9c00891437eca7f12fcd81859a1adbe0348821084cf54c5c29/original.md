```
accessible(accessibility_grid, xf)
accessible(accessibility_grid, xf, repfactors)
```

Using `accessibility_grid`, determine if fractional coordinate `xf` (relative to `accessibility_grid.box` is accessible or not. Here, we search for the nearest grid point. We then look at the accessibility of this nearest grid point and all surroudning 9 other grid points. The point `xf` is declared inaccessible if and only if all 10 of these grid points are inaccessible. We take this approach because, if the grid is coarse, we can allow energy computations to automatically determine accessibility at the boundary of accessibility e.g. during a molecular simulation where inaccessible pockets are blocked.

If a tuple of replication factors are also passed, it is assumed that the passed `xf` is relative to a replicated `accessibility_grid.box` so that `xf` is scaled by these rep. factors. So `xf = [0.5, 0.25, 0.1]` with `repfactors=(1, 2, 4)` actually is, relative to `accessibility_grid.box`, fractional coordinate `[0.5, 0.5, 0.4]`.
