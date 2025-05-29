```
plot(x[, y, spec; kwargs...])
plot(x1, y1, x2, y2...; kwargs...)
plot(x1, y1, spec1...; kwargs...)
```

Draw one or more line plots.

Lines are defined by the `x` and `y` coordinates of the connected points, given as numeric vectors, and optionally the format string `spec` that defines the line and marker style and color as in [matplotlib](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.plot.html).

The `y` vector can be replaced by a callable that defines the Y coordinates as a function of the X coordinates.

Multiple lines can be defined by pairs of `x` and `y` coordinates (and optionally their format strings), passed sequentially as arguments of `plot`. Alternatively, if various lines have the same X coordinates, their Y values can be grouped as columns in a matrix.

If no `spec` is given, the series will be plotted as solid lines with a predefined sequence of colors.

Additionally, specifications of lines and markers can be defined by keyword arguments:

  * `linewidth`: line width scale factor.
  * `markersize`: marker size scale factor.
  * `linecolor`: hexadecimal RGB color code for the line.
  * `markercolor`: hexadecimal RGB color code for the markers.

This function can receive a single numeric vector or matrix, which will be interpreted as the Y coordinates; in such case the X coordinates will be a sequence of integers starting at 1.

# Examples

```julia
# Create example data
x = LinRange(-2, 2, 40)
f(t) = t^3 + t^2 + t
y = f.(x)
# Plot x and y
plot(x, y)
# Plot x using the callable
plot(x, f)
# Plot y, using its indices for the x values
plot(y)
# Plot two columns
plot(x, [y 3x.^2 .- 3])
# Plot various series them with custom line specs
y2 = 3x.^2 .- 3
plot(x, y, "-r", x, y2, ":*b")

```
