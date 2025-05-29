```
getcrs([T], las::LAS)
```

Obtain the coordinate reference system (CRS) of a [`LAS`](@ref), either in the format contained in the `LAS` or converted to the type `T`. The LAS format stores CRS data either in the binary format defined by the [GeoTIFF standard](https://docs.ogc.org/is/19-008r4/19-008r4.html) or using the well-known text (WKT) representation defined in the [OpenGIS® Coordinate Transformation Service Standard](https://www.ogc.org/standards/ct/). The former is represented by the custom `GeoKeys` type while the latter is represented by a `String`. Currently, only the conversion from `GeoKeys` to a WKT `String` is implemented, but this allows passing CRS information obtained with `getcrs(String, las)` to other libraries such as [Proj.jl](https://github.com/JuliaGeo/Proj.jl). Note however that the conversion does a strict interpretation of the `GeoKeys` data and may not be able to convert incomplete/non-standard CRS data.
