```
UTMZfromLLA(datum)
```

Construct a `Transformation` object to convert from global `LLA` coordinates to global `UTMZ` coordinates. The zone and hemisphere is automatically calculated following the standard definitions (including exceptions in Norway). Pre-caches ellipsoidal parameters for efficiency and performs Charles Karney's accurate 6th-order series expansion algorithm.

(See also `UTMfromLLA`)
