```
intersects(geom1, geom2)
```

### Parameters

  * `geom1`: the geometry. This can either be a GDAL AbstractGeometry or a GMTdataset (or vector of it), or a Matrix
  * `geom2`: Second geometry. AbstractGeometry if `geom1::AbstractGeometry` or a GMTdataset/Matrix if `geom1` is GMT type

Returns whether the geometries intersect

Determines whether two geometries intersect. If GEOS is enabled, then this is done in rigorous fashion otherwise `true` is returned if the envelopes (bounding boxes) of the two geometries overlap.
