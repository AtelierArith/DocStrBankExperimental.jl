```
load_map_from_json!(m::KeplerGLMap, json_map_file::String)
```

Loads a kepler.gl map file from `json_map_file` into the map `m`. Overwrites any existing map config and datasets.

# Required Arguments

  * `m::KeplerGLMap`: the map to which the config and data should be applied.
  * `json_map_file::String`: the path to the kepler.gl JSON map file.
