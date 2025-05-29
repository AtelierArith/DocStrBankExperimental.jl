```
convexhull(geom; gdataset=false)
```

### Parameters

  * `geom`: the geometry. This can either be a GDAL AbstractGeometry or a GMTdataset (or vector of it), or a Matrix
  * `gdataset`: Returns a GDAL IGeometry even when input are GMTdataset or Matrix

A new geometry object is created and returned containing the convex hull of the geometry on which the method is invoked.

### Returns

A GMT dataset when input is a Matrix or a GMT type (except if `gdaset=true`), or a GDAL IGeometry otherwise
