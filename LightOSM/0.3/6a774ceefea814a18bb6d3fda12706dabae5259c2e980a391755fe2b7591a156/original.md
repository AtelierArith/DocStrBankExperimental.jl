```
buildings_from_object(buildings_json_object::AbstractDict)::Dict{Integer,Building}
```

Creates `Building` objects from data downloaded with `download_osm_buildings`.

# Arguments

  * `buildings_json_object::AbstractDict`: Buildings data downloaded in `:json` format.

# Return

  * `Dict{Integer,Building}`: Mapping from building relation/way ids to `Building` objects.
