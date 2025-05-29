```
tricont(x, y, z; kwargs...)
```

Draw a triangular surface plot.

Either a series of points or a two-dimensional array is drawn as a triangular surface plot. `z` values are interpolated between `x` and `y` values through [Delaunay triangulation](http://mathworld.wolfram.com/DelaunayTriangulation.html).

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
