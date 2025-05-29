```
errorbar(x, y, err[, spec; kwargs...])
errorbar(x, y, errlow, errhigh[, spec; kwargs...])
```

Draw a series of error bars.

Error bars are defined by their `x` and `y` coordinates, and the size of the error bars at either of each `(x, y)` point. For symmetric error bars, only a vector `err` is required, such that their total size will be `2 .* err`. For asymmetric error bars, two vectors `errlow` and `errhigh` are required, such that the size of the error bars will be `errlow .+ errhigh`.

The optional format string `spec` defines the style and color of the lines of error bars and the markers at `(x, y)`, as in [matplotlib](https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.plot.html). If no `specs` are given, the error bars will be plotted as solid lines with a predefined sequence of colors, without markers.

Additionally, the following keyword arguments can be used to modify the aspect of the error bars:

  * `linewidth::Float64`: line width scale factor.
  * `markersize::Float64`: marker size scale factor.
  * `linecolor`: hexadecimal RGB color code for the line.
  * `horizontal::Bool`: set it to `true` to draw horizontal error bars).
  * `capwidth`: fixed value of the width of the bar "caps", in units of   the X axis (or Y axis if `horizontal` is `true`). If it is not given,   the cap width will be automatically adjusted to 0.3 times the mean   separation between data points.

# Examples

```julia
# Create example data
x = LinRange(-2, 2, 10)
y = x.^3 .+ x.^2 .+ x .+ 6
err = LinRange(0.5, 3, 10)
# Draw symmetric, horizontal error bars
errorbar(x, y, err, horizontal=true)
# Draw asymmetric error bars with markers
errorbar(x, y, err, err./2, "-o")

```
