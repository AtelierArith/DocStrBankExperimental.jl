```
buildings_from_file(file_path::String)::Dict{Integer,Building}
```

Creates `Building` objects from OpenStreetMap data file (either `:osm`, `:xml` or `:json` format).

# Arguments

  * `file_path::String`: Path to OpenStreetMap data file.

# Return

  * `Dict{Integer,Building}`: Mapping from building relation/way ids to `Building` objects.
