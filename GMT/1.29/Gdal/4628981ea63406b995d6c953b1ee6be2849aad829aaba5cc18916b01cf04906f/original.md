```
delaunay(geom::AbstractGeometry, tol::Real=0, onlyedges::Bool=true; gdataset=false)
```

### Parameters

  * `geom`: the geometry.
  * `tol`: optional snapping tolerance to use for improved robustness
  * `onlyedges`: if `true`, will return a MULTILINESTRING, otherwise it   will return a GEOMETRYCOLLECTION containing triangular POLYGONs.
  * `gdataset`: Returns a GDAL IGeometry even when input is GMTdataset or Matrix

Return a Delaunay triangulation of the vertices of the geometry.
