```
overlaps(geom1, geom2)
```

### Parameters

  * `geom1`: the geometry. This can either be a GDAL AbstractGeometry or a GMTdataset (or vector of it), or a Matrix
  * `geom2`: Second geometry. AbstractGeometry if `geom1::AbstractGeometry` or a GMTdataset/Matrix if `geom1` is GMT type

Returns `true` if the geometries overlap.
