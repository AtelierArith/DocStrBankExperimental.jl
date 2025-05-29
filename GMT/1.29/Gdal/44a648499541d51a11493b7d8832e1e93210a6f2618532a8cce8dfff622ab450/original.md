```
concavehull(geom, ratio, allow_holes::Bool=true; gdataset=false)
```

### Parameters

  * `geom`: the geometry. This can either be a GDAL AbstractGeometry or a GMTdataset (or vector of it), or a Matrix
  * `ratio`: Ratio of the area of the convex hull and the concave hull.
  * `allow_holes`: Whether holes are allowed.
  * `gdataset`: Returns a GDAL IGeometry even when input are GMTdataset or Matrix

### Returns

A GMT dataset when input is a Matrix or a GMT type (except if `gdaset=true`), or a GDAL IGeometry otherwise
