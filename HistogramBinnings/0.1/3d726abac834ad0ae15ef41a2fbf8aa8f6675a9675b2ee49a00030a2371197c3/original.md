Module for constructing edge vectors for histograms.

# Examples

```julia
using StatsBase 
using HistogramBinnings

h = fit(Histogram, LogEdgeVector, values)

# or with a custom edge vector

edges = LogEdgeVector(lo = 1, hi = 1_000_000, nbins = 60)
h = append!(Histogram(edges), values)
```

# Exports

This module exports the following types and functions:

  * `LogEdgeVector`
  * `LinEdgeVector`
  * `midpoints`
