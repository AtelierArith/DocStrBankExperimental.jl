```
graph_from_object(osm_data_object::Union{XMLDocument,Dict};
                  network_type::Symbol=:drive,
                  weight_type::Symbol=:time,
                  graph_type::Symbol=:static,
                  precompute_dijkstra_states::Bool=false,
                  largest_connected_component::Bool=true
                  )::OSMGraph
```

Creates an `OSMGraph` object from download OpenStreetMap network data, use with  `download_osm_network`.

# Arguments

  * `osm_data_object::Union{XMLDocument,Dict}`: OpenStreetMap network data parsed as either    `XMLDocument` or `Dict` object depending on the download method. *NOTE* if you pass in    a `Dict`, the object will be modified to add missing tag information.
  * `network_type::Symbol=:drive`: Network type filter, pick from `:drive`, `:drive_service`,    `:walk`, `:bike`, `:all`, `:all_private`, `:none`, `:rail`, must match the network type    used to download `osm_data_object`.
  * `weight_type::Symbol=:time`: Weight type for graph edges, pick from `:distance` (km),    `:time` (hours), `:lane_efficiency` (time scaled by number of lanes).
  * `graph_type::Symbol=:static`: Type of `Graphs.AbstractGraph`, pick from `:static`    (`StaticDiGraph`), `:light` (`DiGraph`), `:simple_weighted` (`SimpleWeightedDiGraph`),    `:meta` (`MetaDiGraph`).
  * `precompute_dijkstra_states::Bool=false`: Set true to precompute Dijkstra parent states    for every source node in the graph, *NOTE* this may take a while and may not be    possible for graphs with large amount of nodes due to memory limits.
  * `largest_connected_component::Bool=true`: Set true to keep only the largest connected    components in the network.
  * `filter_network_type::Bool=true`: Set true to filter out nodes and edges that do not    match the `network_type` filter. Useful if the network data was downloaded with custom   Overpass filters and/or not generated with LightOSM.

# Return

  * `OSMGraph`: Container for storing OpenStreetMap node-, way-, relation- and graph-related    obejcts.
