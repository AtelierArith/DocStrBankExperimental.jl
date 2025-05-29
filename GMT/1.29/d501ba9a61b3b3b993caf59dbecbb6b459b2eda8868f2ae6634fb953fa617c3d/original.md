```
readgeom(wkt::String; gdataset::Bool=false)
```

  * `wkt`: A string with the a geometry encoded as a WKT string
  * `gdataset`: If set to `true` forces the return of a GDAL dataset instead of a GMT type.

### Returns

A GMTdataset or a GDAL dataset

### Examples

```julia
D = readgeom("POLYGON ((0 0, 0 10, 10 10, 10 0, 0 0))")
```
