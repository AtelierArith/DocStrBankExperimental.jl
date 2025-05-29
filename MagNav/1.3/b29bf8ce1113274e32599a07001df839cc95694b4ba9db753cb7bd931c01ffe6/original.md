```
map2kmz(map_map::Matrix, map_xx::Vector, map_yy::Vector,
        map_kmz::String   = "map.kmz";
        map_units::Symbol = :rad,
        plot_alt::Real    = 0,
        opacity::Real     = 0.75,
        clims::Tuple      = ())
```

Create KMZ file of map for use with Google Earth. Generates an "icon" overlay, thus not suitable for large maps (e.g., > 5 deg x 5 deg).

**Arguments:**

  * `map_map`:   `ny` x `nx` 2D gridded map data
  * `map_xx`:    `nx` map x-direction (longitude) coordinates [rad] or [deg]
  * `map_yy`:    `ny` map y-direction (latitude)  coordinates [rad] or [deg]
  * `map_kmz`:   (optional) path/name of map KMZ file to save (`.kmz` extension optional)
  * `map_units`: (optional) map xx/yy units {`:rad`,`:deg`}
  * `plot_alt`:  (optional) map altitude in Google Earth [m]
  * `opacity`:   (optional) map opacity {0:1}
  * `clims`:     (optional) length-`2` map colorbar limits `(cmin,cmax)`

**Returns:**

  * `nothing`: `map_kmz` is created
