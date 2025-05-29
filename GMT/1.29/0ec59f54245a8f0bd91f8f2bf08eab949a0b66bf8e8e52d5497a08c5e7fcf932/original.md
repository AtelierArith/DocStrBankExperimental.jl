```
dest, azim = geod(lonlat, azim, distance; proj::String="", s_srs::String="", epsg::Integer=0, dataset=false, unit=:m)
```

Solve the direct geodesic problem.

Args:

  * `lonlat`:   - longitude, latitude (degrees). This can be a vector or a matrix with one row only.
  * `azimuth`:  - azimuth (degrees) ∈ [-540, 540)
  * `distance`: - distance to move from (lat,lon); can be vector and can be negative, Default is meters but see `unit`
  * `proj` or `s_srs`:  - the given projection whose ellipsoid we move along. Can be a proj4 string or an WKT
  * `epsg`:     - Alternative way of specifying the projection [Default is WGS84]
  * `dataset`:  - If true returns a GMTdataset instead of matrix
  * `unit`:     - If `distance` is not in meters use one of `unit=:km`, or `unit=:Nautical` or `unit=:Miles`

The `distance` argument can be a scalar, a Vector, a Vector{Vector} or an AbstractRange. The `azimuth` can be a scalar or a Vector. 

When `azimuth` is a Vector we always return a GMTdataset with the multiple lines. Use this together with a non-scalar `distance` to get lines with multiple points along the line. The number of points along line does not need to be the same. For data, give the `distance` as a Vector{Vector} where each element of `distance` is a vector with the distances of the points along a line. In this case the number of `distance` elements must be equal to the number of `azimuth`. 

### Returns

  * dest - destination after moving for [distance] metres in [azimuth] direction.
  * azi  - forward azimuth (degrees) at destination [dest].

## Example: Compute two lines starting at (0,0) with lengths 111100 & 50000, heading at 15 and 45 degrees.

```
dest, = geod([0., 0], [15., 45], [[0, 10000, 50000, 111100.], [0., 50000]])[1]
```
