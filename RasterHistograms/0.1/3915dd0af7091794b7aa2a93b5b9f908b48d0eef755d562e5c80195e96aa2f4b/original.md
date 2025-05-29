```
function RasterLayerHistogram(rs::Raster; closed = :left, nbins = nothing)
function RasterLayerHistogram(rs::Raster, weights::AbstractWeights;
                              closed = :left, nbins = nothing)
function RasterLayerHistogram(rs::Raster, edges::AbstractVector; closed = :left)
function RasterLayerHistogram(rs::Raster, weights::AbstractWeights,
                              edges::AbstractVector; closed = :left)
```

Construct a `RasterLayerHistogram` from a `Raster`. The flattened `Raster` data, with the `missing` values removed, is passed to the `fit(::Histogram)` function from [StatsBase.jl](https://juliastats.org/StatsBase.jl/latest/empirical/) and a `RasterLayerHistogram` type is returned.
