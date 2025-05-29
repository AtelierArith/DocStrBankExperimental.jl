```
map_check(map_map::Map, lat, lon, alt = fill(median(map_map.alt),size(lat)))
```

Check if latitude and longitude points are on given map.

**Arguments:**

  * `map_map`: `Map` magnetic anomaly map struct
  * `lat`:     latitude  [rad]
  * `lon`:     longitude [rad]
  * `alt`:     (optional) altitude [m], only used for `MapS3D`

**Returns:**

  * `bool`: if true, all `lat` & `lon` (& `alt`) points are on `map_map`
