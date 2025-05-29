```
hexbin(x, y; kwargs...)
```

Draw a hexagon binning plot.

Hexagonal binning and the the current colormap are used to display a bi-dimensional series of points given by `x` and `y`. The number of bins is 40 by default; use the keyword argument `nbins` to set it as a different number.

# Examples

```julia
# Create example data
x = randn(100_000)
y = randn(100_000)
# Draw the hexbin plot
hexbin(x, y)

```
