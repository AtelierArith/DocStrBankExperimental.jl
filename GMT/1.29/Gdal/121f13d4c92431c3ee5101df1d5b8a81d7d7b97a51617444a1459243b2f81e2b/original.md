```
pointalongline(geom, distance::Real; gdataset=false)
```

### Parameters

  * `geom`: the geometry. This can either be a GDAL AbstractGeometry or a GMTdataset (or vector of it), or a Matrix
  * `distance`: distance along the curve at which to sample position. This   distance should be between zero and geomlength() for this curve.
  * `gdataset`: Returns a GDAL IGeometry even when input are GMTdataset or Matrix

Fetch point (or NULL) at given distance along curve.

### Returns

A GMT dataset when input is a Matrix or a GMT type (except if `gdaset=true`), or a GDAL IGeometry otherwise
