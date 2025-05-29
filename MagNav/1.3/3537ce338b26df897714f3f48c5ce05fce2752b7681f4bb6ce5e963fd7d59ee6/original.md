```
get_map_val(map_map::Map, lat, lon, alt; α = 200, return_itp::Bool = false)
```

Get scalar magnetic anomaly map values along a flight path. `map_map` is upward and/or downward continued to `alt` as necessary (except if drape map).

**Arguments:**

  * `map_map`:    `Map` magnetic anomaly map struct
  * `lat`:        latitude  [rad]
  * `lon`:        longitude [rad]
  * `alt`:        altitude [m]
  * `α`:          (optional) regularization parameter for downward continuation
  * `return_itp`: (optional) if true, also return `itp_map`

**Returns:**

  * `map_val`: scalar magnetic anomaly map values
  * `itp_map`: if `return_itp = true`, map interpolation function (`f(lat,lon)` or `f(lat,lon,alt)`)
