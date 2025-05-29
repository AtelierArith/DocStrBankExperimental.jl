```
scatter3(x, y, z[, color; kwargs...])
```

Draw a three-dimensional scatter plot.

Points are defined by their `x`, `y` and `z` coordinates, given as numeric vectors. Additionally, values for markers' `color` can be provided, which will be used in combination with the current colormap.

The last variable can be replaced by a callable that defines it as a function of the previous variables.

# Examples

```julia
# Create example data
x = 2 .* rand(100) .- 1
y = 2 .* rand(100) .- 1
z = 2 .* rand(100) .- 1
c = 999 .* rand(100) .+ 1
# Plot the points with colors
scatter3(x, y, z, c)

```
