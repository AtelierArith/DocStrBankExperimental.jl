```
function loxodrome(lon1,lat1,lon2,lat2; step=0, unit=:m, np=0, proj::String="", epsg::Integer=0)
```

or

```
function loxodrome(D; step=0, unit=:m, np=0, proj::String="", epsg::Integer=0)
```

Generate a loxodrome (rhumb line) on an ellipsoid. Input data can be two or more points. In later case each line segment is descretized at `step` increments,

### Parameters

  * `D`: - the input points. This can either be a 2x2 matrix or a GMTdataset. Note that only the first 2 points are used.
  * `step`:  - Incremental distance at which the segment line is descretized in meters(the default), but see `unit`
  * `unit`:  - If `step` is not in meters use one of `unit=:km`, or `unit=:Nautical` or `unit=:Miles`
  * `np`:    - Number of intermediate points to be generated between end points (alternative to `step`)
  * `proj`  - If line data is in Cartesians but with a known projection pass in a PROJ4 string
  * `epsg`  - Same as `proj` but using an EPSG code

### Returns

A Mx2 matrix with the on lat of the points along the loxodrome when input is a matrix or the 2 pairs of points. A GMTdataset when the input is GMTdataset.

## Example: Compute an loxodrome between points (0,0) and (30,50) discretized at 100 km steps.

```
loxo = loxodrome([0 0; 30 50], step=100, unit=:k);
```
