```
find_minima(metric, surface; radius = 3)
```

Given a matrix `metric`, such as a gradient matrix, find local minima within a window of size `radius` steps. Argument `surface <: SurfaceSpace` must contain  symbol `:A` (an adjacency matrix)
