```
get_cached_map(map_cache::Map_Cache, lat::Real, lon::Real, alt::Real;
               silent::Bool = false)
```

Get cached map at specific location.

**Arguments:**

  * `map_cache`: `Map_Cache` map cache struct
  * `lat`:       latitude  [rad]
  * `lon`:       longitude [rad]
  * `alt`:       altitude  [m]
  * `silent`:    (optional) if true, no print outs

**Returns:**

  * `itp_mapS`: scalar map interpolation function (`f(lat,lon)` at `alt`)
