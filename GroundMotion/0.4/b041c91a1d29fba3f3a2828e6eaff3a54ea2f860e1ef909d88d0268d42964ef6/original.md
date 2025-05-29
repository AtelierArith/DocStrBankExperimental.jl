Mutable type for earthquake location data.

```
Earthquake(lat,lon,depth,local_mag,moment_mag)
```

Latitude and longitude assumes degrees for WGS84 ellipsoid. Depth in km. Mw=0 in case of moment magnitude is not specified.  All fields are ::Float64.
