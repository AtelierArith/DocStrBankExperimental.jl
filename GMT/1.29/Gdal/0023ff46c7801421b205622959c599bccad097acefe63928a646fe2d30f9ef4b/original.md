```
simplify(geom::AbstractGeometry, tol::Real; gdataset=false)
```

Compute a simplified geometry.

### Parameters

  * `geom`: the geometry.
  * `tol`: the distance tolerance for the simplification.

### Keywords

  * `gdataset`: Returns a GDAL IGeometry even when input is GMTdataset or Matrix
