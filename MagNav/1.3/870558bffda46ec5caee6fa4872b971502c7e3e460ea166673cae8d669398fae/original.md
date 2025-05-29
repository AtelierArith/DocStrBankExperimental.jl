```
map_interpolate(mapV::MapV, dim::Symbol = :X, type::Symbol = :cubic)
```

Create map interpolation function, equivalent of griddedInterpolant in MATLAB.

**Arguments:**

  * `mapV`: `MapV` vector magnetic anomaly map struct
  * `dim`:  map dimension to interpolate {`:X`,`:Y`,`:Z`}
  * `type`: (optional) type of interpolation {:linear,:quad,:cubic}

**Returns:**

  * `itp_map`: map interpolation function (`f(yy,xx)`)
