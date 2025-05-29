```
polarhistogram(data; kwargs...)
```

Draw a polar histogram of angle values contained in `data`.

The following keyword arguments can be supplied:

  * `nbins`: Number of bins; by default, or if a number smaller than 1 is given,   the number of bins is computed as `3.3 * log10(n) + 1`,  with `n` being the   number of elements in `data`.
  * `radians`: Set this argument to `false` to pass and show the angles as degrees.   By default, `data` is assumed to be radians and the angular labels of the   grid are presented as factors of π.
  * `fullcircle`: Set this argument to `true` to scale the angular coordinates of   the histogram and make the bars span over the whole circle.
  * `color`: hexadecimal RGB color code for the bars.

!!! note
    Logarithmic and reversed scales ar disabled in polar plots


# Examples

```julia
# Create example data
data = randn(100)
# Draw a polar histogram with 19 bins
polarhistogram(data, nbins = 19, fullcircle=true)

```
