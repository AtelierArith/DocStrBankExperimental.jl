```
centroid(geom; gdataset=false)
```

### Parameters

  * `geom`: the geometry. This can either be a GDAL AbstractGeometry or a GMTdataset (or vector of them), or a Matrix

### Keywords

  * `gdataset`: Returns a GDAL IGeometry even when input is a GMTdataset or Matrix

Compute the geometry centroid.

The centroid is not necessarily within the geometry.

(This method relates to the SFCOM ISurface::get_Centroid() method however the current implementation based on GEOS can operate on other geometry types such as multipoint, linestring, geometrycollection such as multipolygons. OGC SF SQL 1.1 defines the operation for surfaces (polygons). SQL/MM-Part 3 defines the operation for surfaces and multisurfaces (multipolygons).)

### Returns

A GMT dataset when input is a Matrix or a GMT type (except if `gdaset=true`), or a GDAL IGeometry otherwise
