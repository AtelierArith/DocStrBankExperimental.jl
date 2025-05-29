```
get_map_val(map_map_vec::Vector, path::Path, ind = trues(path.N); α = 200)
```

Get scalar magnetic anomaly map values from multiple maps along a flight path. Each map in `map_map_vec` is upward and/or downward continued to `alt` as necessary.

**Arguments:**

  * `map_map_vec`: vector of `Map` magnetic anomaly map structs
  * `path`:        `Path` struct, i.e., `Traj` trajectory struct, `INS` inertial navigation system struct, or `FILTout` filter extracted output struct
  * `ind`:         (optional) selected data indices
  * `α`:           (optional) regularization parameter for downward continuation

**Returns:**

  * `map_vals`: vector of scalar magnetic anomaly map values
