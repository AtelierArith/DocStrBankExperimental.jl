```
slice(A::Union{AbstractRaster,AbstractRasterStack,AbstracRasterSeries}, dims) => RasterSeries
```

いくつかの次元に沿ってスライスビューを取得し、スライスの`RasterSeries`を得ます。

`Raster`または`RasterStack`の場合、指定された次元に沿った`Raster`または`RasterStack`のスライスの`RasterSeries`が返されます。

`RasterSeries`の場合、出力は別のシリーズであり、子オブジェクトがスライスされ、シリーズの次元インデックスは子の次元が組み合わさったものになります。次元が指定されていない`RasterSeries`に対して`slice`を実行すると、シリーズと子オブジェクトの両方で共有される次元に沿ってスライスされます。

警告: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、githubの問題を報告してください。
