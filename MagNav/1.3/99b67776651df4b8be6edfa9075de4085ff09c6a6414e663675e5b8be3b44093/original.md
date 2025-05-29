```
map_check(map_map::Map, path::Path, ind = trues(path.N))
```

Check if latitude and longitude points are on given map.

**Arguments:**

  * `map_map`: `Map` magnetic anomaly map struct
  * `path`:    `Path` struct, i.e., `Traj` trajectory struct, `INS` inertial navigation system struct, or `FILTout` filter extracted output struct
  * `ind`:     (optional) selected data indices

**Returns:**

  * `bool`: if true, all `path`[`ind`] points are on `map_map`
