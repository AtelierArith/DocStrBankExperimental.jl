```
GridHex(startpoint, radius, width=1200.0, height=1200.0)
```

Define a hexagonal grid, to start at `startpoint` and proceed along the x-axis and then along the y-axis, `radius` is the radius of a circle that encloses each hexagon. The distance in `x` between the centers of successive hexagons is:

$\frac{\sqrt{(3)} \text{radius}}{2}$

To get the next point from the grid, use `nextgridpoint(g::Grid)`.

When you run out of grid points, you'll wrap round and start again.
