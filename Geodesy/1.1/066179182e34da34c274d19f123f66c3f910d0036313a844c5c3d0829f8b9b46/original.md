```
LLAfromUTM(zone, isnorth::Bool, datum)
```

Construct a `Transformation` object to convert from `UTM` coordinates in the specified zone and hemisphere (`isnorth = true` or `false`) to global `LLA` coordinates. Pre-caches ellipsoidal parameters for efficiency and performs Charles Karney's accurate 6th-order series expansion algorithm.

(See also `LLAfromUTMZ`)
