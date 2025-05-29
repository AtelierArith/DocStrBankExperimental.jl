```
geodesicarea(geom)
```

Compute geometry area, considered as a surface on the underlying ellipsoid of the SRS attached to the geometry. The returned area will always be in square meters, and assumes that polygon edges describe geodesic lines on the ellipsoid. If the geometry' SRS is not a geographic one, geometries are reprojected to the underlying geographic SRS of the geometry' SRS.

### Parameters

  * `geom`: the geometry. This can either be a GDAL AbstractGeometry or a GMTdataset (or vector of it), or a Matrix

Returns the area of the geometry in square meters or a negative value in case of error for unsupported geometry types.
