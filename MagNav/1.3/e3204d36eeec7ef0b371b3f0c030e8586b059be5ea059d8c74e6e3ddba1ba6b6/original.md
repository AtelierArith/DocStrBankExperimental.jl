```
get_map(map_file::String   = namad,
        map_field::Symbol  = :map_data;
        map_info::String   = splitpath(map_file)[end],
        map_units::Symbol  = :rad,
        file_units::Symbol = :deg,
        flip_map::Bool     = false)
```

Get map data from saved HDF5 or MAT file or folder containing CSV files. Maps are typically saved in `:deg` units, while `:rad` is used internally.

**Arguments:**

  * `map_file`:   path/name of map data HDF5 or MAT file (`.h5` or `.mat` extension required) or folder containing CSV files
  * `map_field`:  (optional) struct field within MAT file to use, not relevant for CSV or HDF5 file
  * `map_info`:   (optional) map information, only used if not in `map_file`
  * `map_units`:  (optional) map xx/yy units to use in `map_map` {`:rad`,`:deg`}
  * `file_units`: (optional) map xx/yy units used in `map_file` {`:rad`,`:deg`}
  * `flip_map`:   (optional) if true, vertically flip data from map file (possibly useful for CSV map)

**Returns:**

  * `map_map`: `Map` magnetic anomaly map struct
