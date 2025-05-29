```
function geodesic(D; step=0, unit=:m, np=0, proj::String="", epsg::Integer=0, longest::Bool=false)
```

or

```
function geodesic(lon1, lat1, lon2, lat2; step=0, unit=:m, np=0, proj::String="", epsg::Integer=0, longest::Bool=false)
```

Generate geodesic line(s) (shortest distace) on an ellipsoid. Input data can be two or more points. In later case each line segment is descretized at `step` increments,

### Parameters

  * `D`: - the input points. This can either be a GMTdataset (or vector of it), a Mx2 matrix, the name        of file that can be read as a GMTdataset by `gmtread()` or a GDAL AbstractDataset object
  * `step`: - Incremental distance at which the segment line is descretized in meters(the default), but see `unit`
  * `unit`: - If `step` is not in meters use one of `unit=:km`, or `unit=:Nautical` or `unit=:Miles`
  * `np`:   - Number of intermediate points between poly-line vertices (alternative to `step`)
  * `proj`  - If line data is in Cartesians but with a known projection pass in a PROJ4 string
  * `epsg`  - Same as `proj` but using an EPSG code
  * `longest` - Compute the 'long way around' of the geodesic. That is, going from point A to B taking             the longest path. But mind you that geodesics other than meridians and equator are not closed             paths (see https://en.wikipedia.org/wiki/Geodesics*on*an*ellipsoid). This line is obtained by             computing the azimuth from A to B, at B, and start the line at B with that azimuth and go around             the Earth till we reach, _close* to A, but not exactly A (except for the simple meridian cases).

### Returns

A Mx2 matrix with the lon lat of the points along the geodesic when input is a matrix. A GMT dataset or a vector of it (when input is Vector{GMTdataset}).

## Example: Compute an geodesic between points (0,0) and (30,50) discretized at 100 km steps.

```
mat = geodesic([0 0; 30 50], step=100, unit=:k);
```
