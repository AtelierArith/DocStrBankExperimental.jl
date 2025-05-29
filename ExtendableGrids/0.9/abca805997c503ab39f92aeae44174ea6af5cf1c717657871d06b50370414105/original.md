```
u_to=interpolate(grid_to, u_from, grid_from;eps=1.0e-14,trybrute=true)
```

Piecewise linear interpolation of function `u_from` on grid `grid_from` to `grid_to`. Works for matrices with second dimension corresponding to grid nodes and for vectors.

!!! warning
    May be slow on non-convex domains. If `trybrute==false` it may even fail.


!!! warning
    Currently implemented for simplex grids only.

