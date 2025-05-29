```
buildings_from_object(buildings_xml_object::XMLDocument)::Dict{Integer,Building}
```

Creates `Building` objects from data downloaded with `download_osm_buildings`.

# Arguments

  * `buildings_xml_object::XMLDocument`: Buildings data downloaded in `:xml` or `:osm` format.

# Return

  * `Dict{Integer,Building}`: Mapping from building relation/way ids to `Building` objects.
