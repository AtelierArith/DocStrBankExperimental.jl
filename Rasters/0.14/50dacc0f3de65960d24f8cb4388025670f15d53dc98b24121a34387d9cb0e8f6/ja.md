```
Projected <: AbstractProjected

Projected(order, span, sampling, crs, mappedcrs)
Projected(; order=AutoOrder(), span=AutoSpan(), sampling=AutoSampling(), crs, mappedcrs=nothing)
```

プロジェクションが付加された [`AbstractSampled`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.AbstractSampled) `Lookup`。

フィールドと動作は、`crs` および `mappedcrs` フィールドの追加を除いて、[`Sampled`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.Sampled) と同じです。

`crs` と `mappedcrs` フィールドの両方に CRS データ（GeoFormatTypes.jl の `GeoFormat` ラッパー内）が含まれている場合、セレクター入力とプロット軸は指定された `mappedcrs` プロジェクションに自動的に変換されます。一般的な使用例は、例えば GDALarray を読み込む際にコンストラクタに `mappedcrs=EPSG(4326)` を渡すことです：

```julia
GDALarray(filename; mappedcrs=EPSG(4326))
```

基礎となる `crs` は GDAL によって検出されます。

`mappedcrs` が指定されていない場合（つまり、`mappedcrs=nothing`）、ベースインデックスがプロットに表示され、セレクターはその形式を使用する必要があります。
