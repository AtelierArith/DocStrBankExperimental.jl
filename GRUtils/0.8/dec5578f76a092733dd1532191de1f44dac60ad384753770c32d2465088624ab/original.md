```
tricont(x, y, z; kwargs...)
```

Draw a triangular contour plot.

The current colormap is used to display a series of points as a triangular contour plot. `z` values are interpolated between `x` and `y` values through [Delaunay triangulation](http://mathworld.wolfram.com/DelaunayTriangulation.html).

The number of contour lines can be set by the keyword argument `levels` (by default `levels = 20`).

!!! note
    If the series of points is concave, there may be interpolation artifacts on the edges of the plot, as the interpolation may occur in very acute triangles.


# Examples

```julia
# Create example point data
x = 8 .* rand(100) .- 4
y = 8 .* rand(100) .- 4
z = sin.(x) + cos.(y)
# Tricontour plot
tricont(x, y, z)

```
