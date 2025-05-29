```
save_map(map_map::Map, map_h5::String = "map_data.h5";
         map_border::Matrix = zeros(eltype(map_map.alt),1,1),
         map_units::Symbol  = :rad,
         file_units::Symbol = :deg)
```

Save map data to HDF5 file. Maps are typically saved in `:deg` units, while `:rad` is used internally.

**Arguments:**

  * `map_map`:    `Map` magnetic anomaly map struct
  * `map_h5`:     (optional) path/name of map data HDF5 file to save (`.h5` extension optional)
  * `map_border`: (optional) [xx yy] border for valid (not filled-in) map data [rad] or [deg]
  * `map_units`:  (optional) map xx/yy units used in `map_map` {`:rad`,`:deg`}
  * `file_units`: (optional) map xx/yy units to use in `map_h5` {`:rad`,`:deg`}

**Returns:**

  * `nothing`: `map_h5` is created
