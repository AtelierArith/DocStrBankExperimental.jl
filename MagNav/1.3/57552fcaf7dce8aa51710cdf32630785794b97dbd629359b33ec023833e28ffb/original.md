```
map2kmz(mapS::Union{MapS,MapSd,MapS3D},
        map_kmz::String = "map.kmz";
        use_mask::Bool  = true,
        plot_alt::Real  = 0,
        opacity::Real   = 0.75,
        clims::Tuple    = ())
```

Create KMZ file of map for use with Google Earth. Generates an "icon" overlay, thus not suitable for large maps (e.g., > 5 deg x 5 deg).

**Arguments:**

  * `mapS`:     `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct
  * `map_kmz`:  (optional) path/name of map KMZ file to save (`.kmz` extension optional)
  * `use_mask`: (optional) if true, apply `mapS` mask to map
  * `plot_alt`: (optional) map altitude in Google Earth [m]
  * `opacity`:  (optional) map opacity {0:1}
  * `clims`:    (optional) length-`2` map colorbar limits `(cmin,cmax)`

**Returns:**

  * `nothing`: `map_kmz` is created
