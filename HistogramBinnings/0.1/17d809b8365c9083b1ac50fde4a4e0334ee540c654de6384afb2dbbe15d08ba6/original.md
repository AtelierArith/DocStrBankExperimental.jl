```
LinEdgeVector{T}(; lo = 1, hi = 10, nbins::Integer) where T <: Real
```

Construct a linearly spaced edge vector of type `T`. The edges are spaced evenly in linear space. `lo` and `hi` are the lower and upper limits of the histogram. `nbins` is the number of bins.

# Examples

```julia
using HistogramBinnings

edges = LinEdgeVector(lo = 1, hi = 1_000_000, nbins = 60)
```
