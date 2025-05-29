```
ENUfromECEF(origin, datum)
ENUfromECEF(origin::UTM, zone, isnorth, datum)
ENUfromECEF(origin::ECEF, lat, lon)
```

Construct a `Transformation` object to convert from global `ECEF` coordinates to local `ENU` coordinates centered at the `origin`. This object pre-caches both the ECEF coordinates and latitude and longitude of the origin for maximal efficiency.
