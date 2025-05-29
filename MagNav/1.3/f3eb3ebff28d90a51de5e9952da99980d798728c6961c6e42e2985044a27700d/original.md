```
save_map(map_map, map_xx, map_yy, map_alt, map_h5::String = "map_data.h5";
         map_info::String   = "Map",
         map_mask::BitArray = falses(1,1),
         map_border::Matrix = zeros(eltype(map_alt),1,1),
         map_units::Symbol  = :rad,
         file_units::Symbol = :deg)
```

Save map data to HDF5 file. Maps are typically saved in `:deg` units, while `:rad` is used internally.

**Arguments:**

  * `map_map`:   `ny` x `nx` (x `nz`) 2D or 3D gridded map data
  * `map_xx`:    `nx` map x-direction (longitude) coordinates [rad] or [deg]
  * `map_yy`:    `ny` map y-direction (latitude)  coordinates [rad] or [deg]
  * `map_alt`:    map altitude(s) or `ny` x `nx` 2D gridded altitude map data [m]
  * `map_h5`:     (optional) path/name of map data HDF5 file to save (`.h5` extension optional)
  * `map_info`:   (optional) map information
  * `map_mask`:   (optional) `ny` x `nx` (x `nz`) mask for valid (not filled-in) map data
  * `map_border`: (optional) [xx yy] border for valid (not filled-in) map data [rad] or [deg]
  * `map_units`:  (optional) map xx/yy units used in `map_xx` & `map_yy` {`:rad`,`:deg`}
  * `file_units`: (optional) map xx/yy units to use in `map_h5` {`:rad`,`:deg`}

**Returns:**

  * `nothing`: `map_h5` is created
