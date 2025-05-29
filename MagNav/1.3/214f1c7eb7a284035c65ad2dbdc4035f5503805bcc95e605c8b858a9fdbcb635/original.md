```
map_utm2lla(mapS::Union{MapS,MapSd,MapS3D};
            zone_utm::Int  = 18,
            is_north::Bool = true,
            save_h5::Bool  = false
            map_h5::String = "map_data.h5")
```

Convert map grid from `UTM` to `LLA`.

**Arguments:**

  * `mapS`:     `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct on `UTM` grid
  * `zone_utm`: (optional) UTM zone
  * `is_north`: (optional) if true, map is in northern hemisphere
  * `save_h5`:  (optional) if true, save `mapS` to `map_h5`
  * `map_h5`:   (optional) path/name of map data HDF5 file to save (`.h5` extension optional)

**Returns:**

  * `mapS`: `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct on `LLA` grid
