```
polygonize(geom; gdataset=false)
```

### Parameters

  * `geom`: the geometry. This can either be a GDAL AbstractGeometry or a GMTdataset (or vector of it), or a Matrix
  * `gdataset`: Returns a GDAL IGeometry even when input are GMTdataset or Matrix

Polygonizes a set of sparse edges.

A new geometry object is created and returned containing a collection of reassembled Polygons: NULL will be returned if the input collection doesn't correspond to a MultiLinestring, or when reassembling Edges into Polygons is impossible due to topological inconsistencies.

### Returns

A GMT dataset when input is a Matrix or a GMT type (except if `gdaset=true`), or a GDAL IGeometry otherwise
