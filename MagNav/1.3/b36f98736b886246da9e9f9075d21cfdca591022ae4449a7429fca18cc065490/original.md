```
map_trim(map_map::Map;
         pad::Int          = 0,
         xx_lim::Tuple     = (-Inf,Inf),
         yy_lim::Tuple     = (-Inf,Inf),
         zone_utm::Int     = 18,
         is_north::Bool    = true,
         map_units::Symbol = :rad,
         silent::Bool      = true)
```

Trim map by removing large areas that are missing map data. Returns trimmed magnetic anomaly map struct.

**Arguments:**

  * `map_map`:   `Map` magnetic anomaly map struct
  * `pad`:       (optional) minimum padding (grid cells) along map edges
  * `xx_lim`:    (optional) x-direction map limits `(xx_min,xx_max)` [rad] or [deg] or [m]
  * `yy_lim`:    (optional) y-direction map limits `(yy_min,yy_max)` [rad] or [deg] or [m]
  * `zone_utm`:  (optional) UTM zone, only used if `map_units = :utm`
  * `is_north`:  (optional) if true, map is in northern hemisphere, only used if `map_units = :utm`
  * `map_units`: (optional) map xx/yy units {`:rad`,`:deg`,`:utm`}
  * `silent`:    (optional) if true, no print outs

**Returns:**

  * `map_map`: `Map` magnetic anomaly map struct, trimmed
