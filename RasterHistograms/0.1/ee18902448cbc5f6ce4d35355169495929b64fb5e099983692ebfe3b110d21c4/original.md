```
function RasterStackHistogram(stack::RasterStack; closed = :left, nbins = nothing)
function RasterStackHistogram(stack::RasterStack, weights::AbstractWeights;
                              closed = :left, nbins = nothing)
function RasterStackHistogram(stack::RasterStack, edges::NTuple{N, AbstractVector};
                              closed = :left)
function RasterStackHistogram(stack::RasterStack, weights::AbstractWeights,
                              edges::NTuple{N, AbstractVector}; closed = :left)
```

Construct a `RasterStackHistogram` from a `RasterStack`. The resulting `Histogram` is N-dimensional, where N is the number of layers. The flattened `Raster` data for each layer, with the`missing` values removed, is passed to the `fit(::Histogram)` function from [StatsBase.jl](https://juliastats.org/StatsBase.jl/latest/empirical/) and a `RasterStackHistogram` type is returned.
