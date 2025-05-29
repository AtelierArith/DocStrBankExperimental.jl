```
function RasterStackHistogram(stack::RasterStack; closed = :left, nbins = nothing)
function RasterStackHistogram(stack::RasterStack, weights::AbstractWeights;
                              closed = :left, nbins = nothing)
function RasterStackHistogram(stack::RasterStack, edges::NTuple{N, AbstractVector};
                              closed = :left)
function RasterStackHistogram(stack::RasterStack, weights::AbstractWeights,
                              edges::NTuple{N, AbstractVector}; closed = :left)
```

`RasterStack`から`RasterStackHistogram`を構築します。結果として得られる`Histogram`はN次元であり、Nはレイヤーの数です。各レイヤーのフラット化された`Raster`データは、`missing`値が削除された状態で、[StatsBase.jl](https://juliastats.org/StatsBase.jl/latest/empirical/)の`fit(::Histogram)`関数に渡され、`RasterStackHistogram`型が返されます。
