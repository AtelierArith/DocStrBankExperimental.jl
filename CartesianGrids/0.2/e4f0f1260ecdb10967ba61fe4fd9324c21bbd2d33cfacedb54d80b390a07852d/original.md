```
origin(g::PhysicalGrid) -> Tuple{Int,Int}
```

Return a tuple of the indices of the primal node that corresponds to the physical origin of the coordinate system used by `g`. Note that these indices need not lie inside the range of indices occupied by the grid. For example, if the range of physical coordinates occupied by the grid is (1.0,3.0) x (2.0,4.0), then the origin is not inside the grid.
