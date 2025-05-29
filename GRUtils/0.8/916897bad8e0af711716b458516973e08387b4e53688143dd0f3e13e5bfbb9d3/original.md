```
histogram(data; kwargs...)
```

Draw a histogram of `data`.

The following keyword arguments can be supplied:

  * `nbins`: Number of bins; by default, or if a number smaller than 1 is given,   the number of bins is computed as `3.3 * log10(n) + 1`,  with `n` being the   number of elements in `data`.
  * `horizontal`: whether the histogram should be horizontal (`false` by default).
  * `color`: hexadecimal RGB color code for the bars.

!!! note
    If the vertical axis (or the horizontal axis if `horizontal == true`) is set in logarithmic scale, the bars of the histogram will start at 1.0.


# Examples

```julia
# Create example data
data = 2 .* randn(100) .- 1
# Draw the histogram with 19 bins
histogram(data, nbins=19)
# Horizontal histogram with log scale
histogram(data, horizontal=true, xlog=true)

```
