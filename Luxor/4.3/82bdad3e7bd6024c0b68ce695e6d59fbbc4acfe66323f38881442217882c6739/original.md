```
GridRect(startpoint, xspacing, yspacing, width, height)
```

Define a rectangular grid, to start at `startpoint` and proceed along the x-axis in steps of `xspacing`, then along the y-axis in steps of `yspacing`.

```
GridRect(startpoint, xspacing=100.0, yspacing=100.0, width=1200.0, height=1200.0)
```

For a column, set the `xspacing` to 0:

```
grid = GridRect(O, 0, 40)
```

To get points from the grid, use `nextgridpoint(g::Grid)`.

```julia
julia> grid = GridRect(O, 0, 40);

julia> nextgridpoint(grid)
Point(0.0, 0.0)

julia> nextgridpoint(grid)
Point(0.0, 40.0)
```

When you run out of grid points, you'll wrap round and start again.
