```
map_gxf2h5(map_gxf::String, alt::Real;
           map_info::String = splitpath(map_gxf)[end],
           fill_map::Bool   = true,
           get_lla::Bool    = true,
           zone_utm::Int    = 18,
           is_north::Bool   = true,
           save_h5::Bool    = false,
           map_h5::String   = "map_data.h5")
```

Convert map data file (with assumed `UTM` grid) from GXF to HDF5. The order of operations is:

  * original map from `map_gxf` =>
  * trim away large areas that are missing map data =>
  * fill remaining areas that are missing map data =>
  * convert map grid from `UTM` to `LLA`

Specifically meant for SMALL and LEVEL maps ONLY.

**Arguments:**

  * `map_gxf`:  path/name of target (e.g., magnetic) map GXF file (`.gxf` extension optional)
  * `alt`:      map altitude [m]
  * `map_info`: (optional) map information
  * `fill_map`: (optional) if true, fill areas that are missing map data
  * `get_lla`:  (optional) if true, convert map grid from `UTM` to `LLA`
  * `zone_utm`: (optional) UTM zone
  * `is_north`: (optional) if true, map is in northern hemisphere
  * `save_h5`:  (optional) if true, save `mapS` to `map_h5`
  * `map_h5`:   (optional) path/name of map data HDF5 file to save (`.h5` extension optional)

**Returns:**

  * `mapS`: `MapS` scalar magnetic anomaly map struct
