```
function RasterLayerHistogram(rs::Raster; closed = :left, nbins = nothing)
function RasterLayerHistogram(rs::Raster, weights::AbstractWeights;
                              closed = :left, nbins = nothing)
function RasterLayerHistogram(rs::Raster, edges::AbstractVector; closed = :left)
function RasterLayerHistogram(rs::Raster, weights::AbstractWeights,
                              edges::AbstractVector; closed = :left)
```

`Raster` から `RasterLayerHistogram` を構築します。`missing` 値が削除されたフラットな `Raster` データが、[StatsBase.jl](https://juliastats.org/StatsBase.jl/latest/empirical/) の `fit(::Histogram)` 関数に渡され、`RasterLayerHistogram` 型が返されます。
