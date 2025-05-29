```
get_map_val(map_map::Map, path::Path, ind = trues(path.N);
            α=200, return_itp::Bool = false)
```

Get scalar magnetic anomaly map values along a flight path. `map_map` is upward and/or downward continued to `alt` as necessary.

**Arguments:**

  * `map_map`:    `Map` magnetic anomaly map struct
  * `path`:       `Path` struct, i.e., `Traj` trajectory struct, `INS` inertial navigation system struct, or `FILTout` filter extracted output struct
  * `ind`:        (optional) selected data indices
  * `α`:          (optional) regularization parameter for downward continuation
  * `return_itp`: (optional) if true, also return `map_itp`

**Returns:**

  * `map_val`: scalar magnetic anomaly map values
  * `map_itp`: if `return_itp = true`, map interpolation function (`f(lat,lon)` or `f(lat,lon,alt)`)
