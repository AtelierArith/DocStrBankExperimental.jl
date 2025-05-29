```
buffer(geom, dist::Real, quadsegs::Integer=30; gdataset=false)
```

Compute buffer of a geometry.

### Parameters

  * `geom`: the geometry. This can either be a GDAL AbstractGeometry or a GMTdataset (or vector of it), or a Matrix
  * `dist`: the buffer distance to be applied. Should be expressed into the   same unit as the coordinates of the geometry.
  * `quadsegs`: the number of segments used to approximate a 90 degree (quadrant) of curvature.

### Keywords

  * `gdataset`: Returns a GDAL IGeometry even when input is a GMTdataset or Matrix

Builds a new geometry containing the buffer region around the geometry on which it is invoked. The buffer is a polygon containing the region within the buffer distance of the original geometry.

Some buffer sections are properly described as curves, but are converted to approximate polygons. The `quadsegs` parameter can be used to control how many segments should be used to define a 90 degree curve - a quadrant of a circle. A value of 30 is a reasonable default. Large values result in large numbers of vertices in the resulting buffer geometry while small numbers reduce the accuracy of the result.

### Returns

A GMT dataset when input is a Matrix or a GMT type (except if `gdaset=true`), or a GDAL IGeometry otherwise
