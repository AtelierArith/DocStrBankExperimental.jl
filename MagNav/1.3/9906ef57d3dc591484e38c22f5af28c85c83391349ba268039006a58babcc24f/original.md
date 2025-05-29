```
map_utm2lla(map_map::Matrix, map_xx::Vector, map_yy::Vector,
            alt, map_mask::BitMatrix;
            map_info::String = "Map",
            zone_utm::Int    = 18,
            is_north::Bool   = true,
            save_h5::Bool    = false,
            map_h5::String   = "map_data.h5")
```

Convert map grid from `UTM` to `LLA`.

**Arguments:**

  * `map_map`:  `ny` x `nx` 2D gridded map data on `UTM` grid
  * `map_xx`:   `nx` map x-direction (longitude) coordinates [m]
  * `map_yy`:   `ny` map y-direction (latitude)  coordinates [m]
  * `alt`:      map altitude(s) or altitude map [m]
  * `map_mask`: `ny` x `nx` mask for valid (not filled-in) map data
  * `map_info`: (optional) map information
  * `zone_utm`: (optional) UTM zone
  * `is_north`: (optional) if true, map is in northern hemisphere
  * `save_h5`:  (optional) if true, save map data to `map_h5`
  * `map_h5`:   (optional) path/name of map data HDF5 file to save (`.h5` extension optional)

**Returns:**

  * `map_map`:  `ny` x `nx` 2D gridded map data on `LLA` grid
  * `map_xx`:   `nx` map x-direction (longitude) coordinates [rad]
  * `map_yy`:   `ny` map y-direction (latitude)  coordinates [rad]
  * `map_mask`: `ny` x `nx` mask for valid (not filled-in) map data on `LLA` grid
