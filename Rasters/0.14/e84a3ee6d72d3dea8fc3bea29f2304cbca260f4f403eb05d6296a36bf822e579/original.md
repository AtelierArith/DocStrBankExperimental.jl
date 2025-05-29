```
crs(x::Raster)
```

Get the projected coordinate reference system of a `Y` or `X` `Dimension`, or of the `Y`/`X` dims of an `AbstractRaster`.

For [`Mapped`](@ref) lookup this may be `nothing` as there may be no projected coordinate reference system at all. See [`setcrs`](@ref) to set it manually.
