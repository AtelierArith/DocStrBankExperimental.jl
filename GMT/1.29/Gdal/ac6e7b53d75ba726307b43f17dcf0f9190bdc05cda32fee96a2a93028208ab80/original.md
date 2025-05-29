```
difference(geom1, geom2; gdataset=false)
```

### Parameters

  * `geom1`: the geometry. This can either be a GDAL AbstractGeometry or a GMTdataset (or vector of it), or a Matrix
  * `geom2`: Second geometry. AbstractGeometry if `geom1::AbstractGeometry` or a GMTdataset/Matrix if `geom1` is GMT type

### Keywords

  * `gdataset`: Returns a GDAL IGeometry even when input is GMTdataset or Matrix

Generates a new geometry which is the region of this geometry with the region of the other geometry removed.

### Returns

A GMT dataset when input is a Matrix or a GMT type (except if `gdaset=true`), or a GDAL IGeometry otherwise
