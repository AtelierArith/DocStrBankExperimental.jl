```
Proj(CRS)
Proj(code)
```

Convert the coordinates of geometry or domain to a given coordinate reference system `CRS` or EPSG/ESRI `code`.

Optionally, the transform samples the `boundary` of polytopes, if this option is `true`, to handle distortions that occur in manifold conversions.

## Examples

```julia
Proj(Polar)
Proj(WebMercator)
Proj(Mercator{WGS84Latest})
Proj(EPSG{3395})
Proj(ESRI{54017})
```

### Notes

By default, only the vertices of the polytopes are transformed, disregarding distortions that occur in manifold conversions. To handle this case, use [`TransformedGeometry`](@ref).
