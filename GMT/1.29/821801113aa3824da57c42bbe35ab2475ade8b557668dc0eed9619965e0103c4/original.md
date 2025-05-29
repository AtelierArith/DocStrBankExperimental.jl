```
circgeo(lon, lat; radius=X, proj="", s_srs="", epsg=0, dataset=false, unit=:m, np=120, shape="")
```

Or

```
circgeo(lonlat; radius=X, proj="", s_srs="", epsg=0, dataset=false, unit=:m, np=120, shape="")
```

Compute a geographical circle (and other shapes) in geographical or in projected coordinates.

### Args

  * `lonlat`:   - longitude, latitude (degrees). If a Mx2 matrix, returns as many segments as number of rows.               Use this to compute multiple shapes at different positions. In this case output type is               always a vector of GMTdatasets.

### Kwargs

  * `radius`:   - The circle radius in meters (but see `unit`) or circumscribing circle for the other shapes
  * `proj` or `s_srs`:  - the given projection whose ellipsoid we move along. Can be a proj4 string or an WKT
  * `epsg`:     - Alternative way of specifying the projection [Default is WGS84]
  * `dataset`:  - If true returns a GMTdataset instead of matrix (with single shapes)
  * `unit`:     - If `radius` is not in meters use one of `unit=:km`, or `unit=:Nautical` or `unit=:Miles`
  * `np`:       - Number of points into which the circle is descretized (Default = 120)
  * `shape`:    - Optional string/symbol with "triangle", "square", "pentagon" or "hexagon" (or just the first char)               to compute one of those geometries instead of a circle. `np` is ignored in these cases.

### Returns

  * circ - A Mx2 matrix or GMTdataset with the circle coordinates

### Example:

Compute a circle about the (0,0) point with a radius of 50 km

```julia
    c = circgeo([0. 0], radius=50, unit=:k)
```
