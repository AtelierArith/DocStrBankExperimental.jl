```
map_check(map_map_vec::Vector, path::Path, ind = trues(path.N))
```

Check if latitude and longitude points are on given maps.

**Arguments:**

  * `map_map_vec`: vector of `Map` magnetic anomaly map structs
  * `path`:        `Path` struct, i.e., `Traj` trajectory struct, `INS` inertial navigation system struct, or `FILTout` filter extracted output struct
  * `ind`:         (optional) selected data indices

**Returns:**

  * `bools`: if true, all `path`[`ind`] points are on `map_map_vec`[i]
