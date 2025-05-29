```
KeplerGLMap(token::String;
    width::Int64 = 1200,
    height::Int64 = 900,
    center_map = true,
    read_only = false,
    config = KeplerGLBase.make_static_config())
```

Creates a new `KeplerGLMap`.

# Required Arguments

  * `token::String`: the mapbox token to be used for displaying the map.

# Optional Arguments

  * `width:Int64 = 1200`: width of the map window
  * `height:Int64 = 900`: height of the map window
  * `center_map - true`: whether the map should automatically be centered
  * `read_only = false`: whether the map should be read-only (not editable)
  * `config = KeplerGLBase.make_static_config()`: initial configuration
