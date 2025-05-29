```
path2kml(lat::Vector, lon::Vector, alt::Vector,
         path_kml::String   = "path.kml";
         path_units::Symbol = :rad,
         width::Int         = 3,
         color1::String     = "ff000000",
         color2::String     = "80000000",
         points::Bool       = false)
```

Create KML file of flight path for use with Google Earth.

**Arguments:**

  * `lat`:        latitude  [rad] or [deg]
  * `lon`:        longitude [rad] or [deg]
  * `alt`:        altitude  [m]
  * `path_kml`:   (optional) path/name of flight path KML file to save (`.kml` extension optional)
  * `path_units`: (optional) `lat`/`lon` units {`:rad`,`:deg`}
  * `width`:      (optional) line width
  * `color1`:     (optional) path color
  * `color2`:     (optional) below-path color
  * `points`:     (optional) if true, create points instead of line

**Returns:**

  * `nothing`: `path_kml` is created
