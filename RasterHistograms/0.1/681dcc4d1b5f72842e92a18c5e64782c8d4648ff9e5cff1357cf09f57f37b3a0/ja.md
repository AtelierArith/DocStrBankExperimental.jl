```
function RasterSeriesHistogram(series::RasterSeries, edges::NTuple{N, AbstractVector};
                               closed = :left)
function RasterSeriesHistogram(series::RasterSeries, weights::AbstractWeights,
                               edges::NTuple{N, AbstractVector}; closed = :left)
```

`RasterSeries`から`RasterSeriesHistogram`を構築します。`Histograms`を`merge`するにはビンのエッジが同じでなければならないため、このコンストラクタではエッジを渡す必要があります。このコンストラクタは、すべての`RasterStack`が`RasterSeries`内で同じ次元であると仮定しています。
