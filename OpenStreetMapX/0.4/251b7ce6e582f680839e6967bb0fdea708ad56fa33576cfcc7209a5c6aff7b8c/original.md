```
get_map_data(filepath::String,filename::Union{String,Nothing}=nothing;
             road_levels::Set{Int} = Set(1:length(OpenStreetMapX.ROAD_CLASSES)),
			 use_cache::Bool = true, only_intersections::Bool=true)::MapData
```

High level function - parses .osm file and create the road network based on the map data. This code currently can parse both *.osm and *.pbf (@blegat - thank you!) files. The data type is determined by file extension.

**Arguments**

  * `filepath` : path with an .osm/.pbf file (directory or path to a file)
  * `filename` : name of the file (when the first argument is a directory)
  * `road_levels` : a set with the road categories (see: OpenStreetMapX.ROAD_CLASSES for more informations)
  * `use_cache` : a *.cache file will be crated with a serialized map image in the `datapath` folder
  * `only_intersections` : include only road system data
  * `trim_to_connected_graph`: trim orphan nodes in such way that the map is a strongly connected graph
