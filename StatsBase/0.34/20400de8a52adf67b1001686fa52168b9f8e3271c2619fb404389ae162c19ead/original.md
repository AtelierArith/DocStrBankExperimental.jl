```
fit(Histogram, data[, weight][, edges]; closed=:left[, nbins])
```

Fit a histogram to `data`.

# Arguments

  * `data`: either a vector (for a 1-dimensional histogram), or a tuple of vectors of equal length (for an *n*-dimensional histogram).
  * `weight`: an optional `AbstractWeights` (of the same length as the data vectors), denoting the weight each observation contributes to the bin. If no weight vector is supplied, each observation has weight 1.
  * `edges`: a vector (typically an `AbstractRange` object), or tuple of vectors, that gives the edges of the bins along each dimension. If no edges are provided, they are chosen so that approximately `nbins` bins of equal width are constructed along each dimension.

!!! note
    In most cases, the number of bins will be `nbins`. However, to ensure that the bins have equal width, more or fewer than `nbins` bins may be used.


# Keyword arguments

  * `closed`: if `:left` (the default), the bin intervals are left-closed [a,b); if `:right`, intervals are right-closed (a,b].
  * `nbins`: if no `edges` argument is supplied, the approximate number of bins to use along each dimension (can be either a single integer, or a tuple of integers). If omitted, it is computed using Sturges's formula, i.e. `ceil(log2(length(n))) + 1` with `n` the number of data points.

# Examples

```julia
# Univariate
h = fit(Histogram, rand(100))
h = fit(Histogram, rand(100), 0:0.1:1.0)
h = fit(Histogram, rand(100), nbins=10)
h = fit(Histogram, rand(100), weights(rand(100)), 0:0.1:1.0)
h = fit(Histogram, [20], 0:20:100)
h = fit(Histogram, [20], 0:20:100, closed=:right)

# Multivariate
h = fit(Histogram, (rand(100),rand(100)))
h = fit(Histogram, (rand(100),rand(100)),nbins=10)
```
