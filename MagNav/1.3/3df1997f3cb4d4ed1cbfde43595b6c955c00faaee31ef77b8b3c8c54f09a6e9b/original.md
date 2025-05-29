```
(map_cache::Map_Cache)(lat::Real, lon::Real, alt::Real;
                      silent::Bool = true)
```

Get cached map value at specific location.

**Arguments:**

  * `map_cache`: `Map_Cache` map cache struct
  * `lat`:       latitude  [rad]
  * `lon`:       longitude [rad]
  * `alt`:       altitude  [m]
  * `silent`:    (optional) if true, no print outs

**Returns:**

  * `map_val`: scalar magnetic anomaly map value
