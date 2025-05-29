```
loxodrome_direct(lon, lat, azimuth, distance, a=6378137.0, f=0.0033528106647474805)
```

Compute the direct problem of a loxodrome on the ellipsoid.

Given latitude and longitude of P1, azimuth a12 of the loxodrome P1P2 and the arc length s along the loxodrome curve, compute the latitude and longitude of P2.

Args:

  * `lon, lat`: - longitude, latitude (degrees) of starting point.
  * `azimuth`:  - azimuth (degrees)
  * `distance`: - distance to move from (lat,lon) in meters
  * `a` - major axis of the ellipsoid (meters). Default values for WGS84
  * `f` - flattening od the ellipsoid (default = 1 / 298.257223563)

### Returns

  * [lon lat] of destination after moving for [distance] metres in [azimuth] direction.

## Example: Compute the end point at a bearing of 45 degrees 10000 meters from point 0,0

```
loxo = loxodrome_direct(0,0,45, 10000)
```
