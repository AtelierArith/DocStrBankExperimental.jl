```
function loxodrome_inverse(lon1, lat1, lon2, lat2, a=6378137.0, f=0.0033528106647474805)
```

Compute the inverse problem of a loxodrome on the ellipsoid.

Given latitudes and longitudes of P1 and P2 on the ellipsoid, compute the azimuth a12 of the loxodrome P1P2, the arc length s along the loxodrome curve.

Args:

  * `lon1, lat1, lon2, lat2`: - longitude and latitude of starting and end points (degrees).
  * `a` - major axis of the ellipsoid (meters). Default values for WGS84
  * `f` - flattening od the ellipsoid (default = 1 / 298.257223563)

### Returns

  * Distance (meters) and azimuth from P1 to P2

## Example: Compute the distance and azimuth beyween points (0,0) and (5,5)

```
dist, azim = loxodrome_inverse(0,0,5,5)
```
