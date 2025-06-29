```
xEast, yNorth, zUp = geodetic2enu(lon, lat, h, lon0, lat0, h0)
```

Convert from geodetic coordinates to local East, North, Up (ENU) coordinates.

  * `lon`: a scalar, or vector of longitudes to be transformed
  * `lat`: a scalar, or vector of latitudes to be transformed
  * `h`: a scalar, or vector of altitudes of the point(s) to be transformed
  * `lon0, lat0, h0`: Origin of the geodetic coordinates system (all 3 scalars)

Returns three Float64 scalars or three vectors with the cartesian ENU components
