```
scatter(x[, y, size, color; kwargs...])
```

Draw a scatter plot.

Points are defined by their `x` and `y` coordinates, given as numeric vectors. Additionally, values for markers' `size` and `color` can be provided. Size values will determine the marker size in percent of the regular size, and color values will be used in combination with the current colormap.

The last variable can be replaced by a callable that defines it as a function of the previous variables.

This function can receive a single numeric vector or matrix, which will be interpreted as the Y coordinates; in such case the X coordinates will be a sequence of integers starting at 1.

# Examples

```julia
# Create example data
x = LinRange(0, 1, 11)
y = LinRange(0, 1, 11)
s = LinRange(50, 400, 11)
c = LinRange(0, 255, 11)
# Plot the points with increasing size and color
scatter(x, y, s, c)

```
