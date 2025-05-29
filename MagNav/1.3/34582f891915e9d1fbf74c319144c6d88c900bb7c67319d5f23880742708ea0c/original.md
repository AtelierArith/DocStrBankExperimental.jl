```
map_trim(map_map::Map, path::Path;
         pad::Int          = 0,
         zone_utm::Int     = 18,
         is_north::Bool    = true,
         map_units::Symbol = :rad,
         silent::Bool      = true)
```

Trim map by removing large areas far away from `path`. Do not use prior to upward continuation, as this causes in edge effect errors. Returns trimmed magnetic anomaly map struct.

**Arguments:**

  * `map_map`:   `Map` magnetic anomaly map struct
  * `path`:      `Path` struct, i.e., `Traj` trajectory struct, `INS` inertial navigation system struct, or `FILTout` filter extracted output struct
  * `pad`:       (optional) minimum padding (grid cells) along map edges
  * `zone_utm`:  (optional) UTM zone, only used if `map_units = :utm`
  * `is_north`:  (optional) if true, map is in northern hemisphere, only used if `map_units = :utm`
  * `map_units`: (optional) map xx/yy units {`:rad`,`:deg`,`:utm`}
  * `silent`:    (optional) if true, no print outs

**Returns:**

  * `map_map`: `Map` magnetic anomaly map struct, trimmed
