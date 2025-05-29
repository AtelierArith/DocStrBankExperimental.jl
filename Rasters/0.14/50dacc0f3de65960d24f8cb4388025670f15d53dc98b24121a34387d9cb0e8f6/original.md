```
Projected <: AbstractProjected

Projected(order, span, sampling, crs, mappedcrs)
Projected(; order=AutoOrder(), span=AutoSpan(), sampling=AutoSampling(), crs, mappedcrs=nothing)
```

An [`AbstractSampled`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.AbstractSampled) `Lookup` with projections attached.

Fields and behaviours are identical to [`Sampled`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.Sampled) with the addition of `crs` and `mappedcrs` fields.

If both `crs` and `mappedcrs` fields contain CRS data (in a `GeoFormat` wrapper from GeoFormatTypes.jl) the selector inputs and plot axes will be converted from and to the specified `mappedcrs` projection automatically. A common use case would be to pass `mappedcrs=EPSG(4326)` to the constructor when loading eg. a GDALarray:

```julia
GDALarray(filename; mappedcrs=EPSG(4326))
```

The underlying `crs` will be detected by GDAL.

If `mappedcrs` is not supplied (ie. `mappedcrs=nothing`), the base index will be shown on plots, and selectors will need to use whatever format it is in.
