Draw a three-dimensional surface plot.

This function uses the current colormap to display a either a series of points or a two-dimensional array as a surface plot. It can receive one or more of the following:

  * x values, y values and z values, or
  * M x values, N y values and z values on a NxM grid, or
  * M x values, N y values and a callable to determine z values

If a series of points is passed to this function, their values will be interpolated on a grid. For grid points outside the convex hull of the provided points, a value of 0 will be used.

:param args: the data to plot

**Usage examples:**

.. code-block:: julia

```
julia> # Create example point data
julia> x = 8 .* rand(100) .- 4
julia> y = 8 .* rand(100) .- 4
julia> z = sin.(x) .+ cos.(y)
julia> # Draw the surface plot
julia> surface(x, y, z)
julia> # Create example grid data
julia> x = LinRange(-2, 2, 40)
julia> y = LinRange(0, pi, 20)
julia> z = sin.(x') .+ cos.(y)
julia> # Draw the surface plot
julia> surface(x, y, z)
julia> # Draw the surface plot using a callable
julia> surface(x, y, (x,y) -> sin(x) + cos(y))
```
