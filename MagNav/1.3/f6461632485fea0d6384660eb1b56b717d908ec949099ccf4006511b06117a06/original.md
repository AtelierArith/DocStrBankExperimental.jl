```
path2kml(path::Path,
         path_kml::String = "path.kml";
         width::Int       = 3,
         color1::String   = "",
         color2::String   = "00ffffff",
         points::Bool     = false)
```

Create KML file of flight path for use with Google Earth.

**Arguments:**

  * `path`:      `Path` struct, i.e., `Traj` trajectory struct, `INS` inertial navigation system struct, or `FILTout` filter extracted output struct
  * `path_kml`:  (optional) path/name of flight path KML file to save (`.kml` extension optional)
  * `width`:     (optional) line width
  * `color1`:    (optional) path color
  * `color2`:    (optional) below-path color
  * `points`:    (optional) if true, create points instead of line

**Returns:**

  * `nothing`: `path_kml` is created
