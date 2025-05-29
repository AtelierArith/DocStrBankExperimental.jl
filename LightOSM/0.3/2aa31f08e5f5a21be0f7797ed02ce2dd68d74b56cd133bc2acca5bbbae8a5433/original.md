```
graph_from_download(download_method::Symbol;
                    network_type::Symbol=:drive,
                    metadata::Bool=false,
                    download_format::Symbol=:json,
                    save_to_file_location::Union{String,Nothing}=nothing,
                    weight_type::Symbol=:time,
                    graph_type::Symbol=:static,
                    precompute_dijkstra_states::Bool=false,
                    largest_connected_component::Bool=true,
                    download_kwargs...
                    )::OSMGraph
```

Downloads OpenStreetMap network data and creates an `OSMGraph` object.

# Arguments

  * `download_method::Symbol`: Download method, choose from `:place_name`, `:bbox` or `:point`.
  * `network_type::Symbol=:drive`: Network type filter, pick from `:drive`, `:drive_service`, `:walk`, `:bike`, `:all`, `:all_private`, `:none`, `:rail`.
  * `metadata::Bool=false`: Set true to return metadata.
  * `download_format::Symbol=:json`: Download format, either `:osm`, `:xml` or `json`.
  * `save_to_file_location::Union{String,Nothing}=nothing`: Specify a file location to save downloaded data to disk.
  * `weight_type::Symbol=:time`: Weight type for graph edges, pick from `:distance` (km), `:time` (hours), `:lane_efficiency` (time scaled by number of lanes).
  * `graph_type::Symbol=:static`: Type of `Graphs.AbstractGraph`, pick from `:static` (StaticDiGraph), `:light` (DiGraph), `:simple_weighted` (SimpleWeightedDiGraph), `:meta` (MetaDiGraph).
  * `precompute_dijkstra_states::Bool=false`: Set true to precompute dijkstra parent states for every source node in the graph, *NOTE* this may take a while and may not be possible for graphs with large amount of nodes due to memory limits.
  * `largest_connected_component::Bool=true`: Set true to keep only the largest connected components in the network.
  * `filter_network_type::Bool=true`: Set true to filter out nodes and edges that do not    match the `network_type` filter after download. You may want to use this with    `download_method=:custom_filters`.

# Required Kwargs for each Download Method

*`download_method=:place_name`*

  * `place_name::String`: Any place name string used as a search argument to the Nominatim API.

*`download_method=:bbox`*

  * `minlat::AbstractFloat`: Bottom left bounding box latitude coordinate.
  * `minlon::AbstractFloat`: Bottom left bounding box longitude coordinate.
  * `maxlat::AbstractFloat`: Top right bounding box latitude coordinate.
  * `maxlon::AbstractFloat`: Top right bounding box longitude coordinate.

*`download_method=:point`*

  * `point::GeoLocation`: Centroid point to draw the bounding box around.
  * `radius::Number`: Distance (km) from centroid point to each bounding box corner.

*`download_method=:polygon`*

  * `polygon::AbstractVector`: Vector of longitude-latitude pairs.

# Network Types

  * `:drive`: Motorways excluding private and service ways.
  * `:drive_service`: Motorways including private and service ways.
  * `:walk`: Walkways only.
  * `:bike`: Cycleways only.
  * `:all`: All motorways, walkways and cycleways excluding private ways.
  * `:all_private`: All motorways, walkways and cycleways including private ways.
  * `:none`: No network filters.
  * `:rail`: Railways excluding proposed and platform.

# Return

  * `OSMGraph`: Container for storing OpenStreetMap node, way, relation and graph related obejcts.
