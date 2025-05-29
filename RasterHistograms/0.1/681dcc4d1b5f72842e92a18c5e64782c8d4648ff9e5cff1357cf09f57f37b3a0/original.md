```
function RasterSeriesHistogram(series::RasterSeries, edges::NTuple{N, AbstractVector};
                               closed = :left)
function RasterSeriesHistogram(series::RasterSeries, weights::AbstractWeights,
                               edges::NTuple{N, AbstractVector}; closed = :left)
```

Construct a `RasterSeriesHistogram` from a `RasterSeries`. Note that to `merge` `Histograms` the bin edges must be the same, so for this constructor the edges must be passed in. This constructor assumes that the dimensions are the same across all `RasterStack`s in the `RasterSeries`.
