```
arcellipse(x0, y0, primary_radius, secondary_radius, start_angle, end_angle; rotation=0, z0=0, inc=2, gdataset=false)
```

### Parameters

  * `x0`: center X
  * `y0`: center Y
  * `primary_radius`: X radius of ellipse.
  * `secondary_radius`: Y radius of ellipse.
  * `start_angle`: angle to first point on arc (clockwise of X-positive)
  * `end_angle`: angle to last point on arc (clockwise of X-positive)

### Keywords

  * `rotation`: rotation of the ellipse clockwise.
  * `z0`: center Z. Optional, if not provided the output is flat 2D
  * `inc`: the largest step in degrees along the arc. Default is 2 degree
  * `gdataset`: Returns a GDAL IGeometry even when input are GMTdataset or Matrix

### Returns

A GMT dataset or a GDAL IGeometry
