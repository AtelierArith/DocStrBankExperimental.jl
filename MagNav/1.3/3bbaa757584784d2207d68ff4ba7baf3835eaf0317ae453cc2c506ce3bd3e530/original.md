```
map_gxf2h5(map_gxf::String, alt_gxf::String, alt::Real;
           map_info::String    = splitpath(map_gxf)[end],
           pad::Int            = 0,
           sub_igrf_date::Real = get_years(2013,293),
           add_igrf_date::Real = -1,
           zone_utm::Int       = 18,
           is_north::Bool      = true,
           fill_map::Bool      = true,
           up_cont::Bool       = true,
           down_cont::Bool     = true,
           get_lla::Bool       = true,
           dz::Real            = 5,
           down_max::Real      = 150,
           α::Real             = 200,
           save_h5::Bool       = false,
           map_h5::String      = "map_data.h5")
```

Convert map data file (with assumed `UTM` grid) from GXF to HDF5. The order of operations is:

  * original map from `map_gxf` =>
  * trim away large areas that are missing map data =>
  * subtract and/or add IGRF to map data =>
  * fill remaining areas that are missing map data =>
  * upward/downward continue to `alt` =>
  * convert map grid from `UTM` to `LLA`

This can be memory intensive, largely depending on the map size and `dz`. If `up_cont = true`, a `MapS` struct is returned. If `up_cont = false`, a `MapSd` struct is returned, which has an included altitude map.

**Arguments:**

  * `map_gxf`:       path/name of target (e.g., magnetic) map GXF file (`.gxf` extension optional)
  * `alt_gxf`:       path/name of altitude map GXF file (`.gxf` extension optional)
  * `alt`:           final map altitude after upward continuation [m], not used for drape map
  * `map_info`:      (optional) map information
  * `pad`:           (optional) minimum padding (grid cells) along map edges
  * `sub_igrf_date`: (optional) date of IGRF core field to subtract [yr], -1 to ignore
  * `add_igrf_date`: (optional) date of IGRF core field to add [yr], -1 to ignore
  * `zone_utm`:      (optional) UTM zone
  * `is_north`:      (optional) if true, map is in northern hemisphere
  * `fill_map`:      (optional) if true, fill areas that are missing map data
  * `up_cont`:       (optional) if true, upward/downward continue to `alt`
  * `down_cont`:     (optional) if true, downward continue if needed, only used if `up_cont = true`
  * `get_lla`:       (optional) if true, convert map grid from `UTM` to `LLA`
  * `dz`:            (optional) upward continuation step size [m]
  * `down_max`:      (optional) maximum downward continuation distance [m]
  * `α`:             (optional) regularization parameter for downward continuation
  * `save_h5`:       (optional) if true, save `mapS` to `map_h5`
  * `map_h5`:        (optional) path/name of map data HDF5 file to save (`.h5` extension optional)

**Returns:**

  * `mapS`: `MapS` or `MapSd` scalar magnetic anomaly map struct
