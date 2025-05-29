```
plot3(x, y, z[, spec; kwargs...])
plot3(x1, y1, z1, x2, y2, z2...; kwargs...)
plot3(x1, y1, z1, spec1...; kwargs...)
```

Draw one or more three-dimensional line plots.

Lines are defined by the `x`, `y` and `z` coordinates of the connected points, given as numeric vectors, and optionally the format string `spec` that defines the line and marker style and color as in [matplotlib](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.plot.html).

The `z` vector can be replaced by a callable that defines the Z coordinates as a function of the X and Y coordinates.

Multiple lines can be defined by triplets of `x`, `y` and `z` coordinates (and optionally their format strings), passed sequentially as arguments of `plot3`.

If no `specs` are given, the series will be plotted as solid lines with a predefined sequence of colors.

Additionally, specifications of lines and markers can be defined by keyword arguments:

  * `linewidth`: line width scale factor.
  * `markersize`: marker size scale factor.
  * `linecolor`: hexadecimal RGB color code for the line.
  * `markercolor`: hexadecimal RGB color code for the markers.

# Examples

```julia
# Create example data
x = LinRange(0, 30, 1000)
y = cos.(x) .* x
z = sin.(x) .* x
# Draw a solid line and another with star markers
# in one of every 10 points
plot3(x, y, z, x[1:10:end], y[1:10:end], z[1:10:end], "p")

```
