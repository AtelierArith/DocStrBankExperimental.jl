```
ECEFfromENU(origin, datum)
ECEFfromENU(origin::UTM, zone, isnorth, datum)
ECEFfromENU(origin::ECEF, lat, lon)
```

Construct a `Transformation` object to convert from local `ENU` coordinates centred at `origin` to global `ECEF` coodinates. This object pre-caches both the ECEF coordinates and latitude and longitude of the origin for maximal efficiency.
