```
stairs(x[, y, spec; kwargs...])
stairs(x1, y1, x2, y2...; kwargs...)
stairs(x1, y1, spec1...; kwargs...)
```

Draw one or more staircase or step plots.

The coordinates and format of the stair outlines are defined as for line plots (cf. [`plot`](@ref)).

Additionally, the keyword argument `where` can be used to define where the "stairs" (vertical discontinuities between Y values) shoud be placed:

  * `where = "pre"` to make the steps stop at each point (`x[i]`, `y[i]`),   starting at the previous `x` coordinate except for the first point.
  * `where = "post"` to make the steps start at each point (`x[i]`, `y[i]`),   stopping at the next `x` coordinate except for the last point.
  * `where = "mid"` (default) to make the steps go through each point (`x[i]`, `y[i]`)   starting and ending in the middle of the surrounding x-intervals,   except for the first and last points.

# Examples

```julia
# Create example data
x = LinRange(-2, 2, 40)
y = x.^3 .+ x.^2 .+ x
# Plot x and y
stairs(x, y)
# Plot y with indices for x values
stairs(y)
# step directly after x each position
stairs(y, where="pre")
# step between two x positions
stairs(y, where="mid")
# step immediately before x each position
stairs(y, where="post")

```
