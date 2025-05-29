```
Mapped <: AbstractProjected

Mapped(order, span, sampling, crs, mappedcrs)
Mapped(; order=AutoOrder(), span=AutoSpan(), sampling=AutoSampling(), crs=nothing, mappedcrs)
```

An [`AbstractSampled`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.AbstractSampled) `Lookup`, where the dimension index has been mapped to another projection, usually lat/lon or `EPSG(4326)`. `Mapped` matches the dimension format commonly used in netcdf files.

Fields and behaviours are identical to [`Sampled`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.Sampled) with the addition of `crs` and `mappedcrs` fields.

The mapped dimension index will be used as for [`Sampled`](https://rafaqz.github.io/DimensionalData.jl/stable/api/reference#DimensionalData.Dimensions.Lookups.Sampled), but to save in another format the underlying `crs` may be used to convert it.
