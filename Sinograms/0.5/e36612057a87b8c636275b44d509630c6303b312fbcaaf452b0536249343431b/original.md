```
parker_weight(rg::SinoGeom, T = Float32)
```

Compute Parker weighting for non-360° orbits. See https://doi.org/10.1118/1.595078. Returns `Matrix{T}` of size:

  * (1,1) for `SinoPar` with typical 180 or 360 orbit
  * (1,na) for `SinoPar` with atypical orbit
  * (1,1) for `SinoFan` with typical 360 orbit
  * (ns,na) for `SinoFan` with typical 360 orbit
