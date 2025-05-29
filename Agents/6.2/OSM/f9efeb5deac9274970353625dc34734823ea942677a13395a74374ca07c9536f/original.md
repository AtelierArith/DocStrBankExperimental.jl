```
OpenStreetMapSpace(path::AbstractString; kwargs...)
```

Create a space residing on the Open Street Map (OSM) file provided via `path`. This space represents the underlying map as a *continuous* entity choosing accuracy over performance. The map is represented as a graph, consisting of nodes connected by edges. Nodes are not necessarily intersections, and there may be multiple nodes on a road joining two intersections. Agents move along the available roads of the map using routing, see below.

The functionality related to Open Street Map spaces is in the submodule `OSM`. An example of its usage can be found in [Zombie Outbreak in a City](@ref).

## The `OSMAgent`

The base properties for an agent residing on an `OSMSpace` are as follows:

```julia
mutable struct Agent <: AbstractAgent
    id::Int
    pos::Tuple{Int,Int,Float64}
end
```

Current `pos`ition tuple is represented as (first intersection index, second intersection index, distance travelled). The indices are the indices of the nodes of the graph that internally represents the map. Functions like [`OSM.nearest_node`](@ref) or [`OSM.nearest_road`](@ref) can help find those node indices from a (lon, lat) real world coordinate. The distance travelled is in the units of `weight_type`. This ensures that the map is a *continuous* kind of space, as an agent can truly be at any possible point on an existing road.

Use [`OSMAgent`](@ref OSM.OSMAgent) for convenience.

## Obtaining map files

Maps files can be downloaded using the functions provided by [LightOSM.jl](https://github.com/DeloitteDigitalAPAC/LightOSM.jl). Agents.jl also re-exports [`OSM.download_osm_network`](@ref), the main function used to download maps and provides a test map in [`OSM.test_map`](@ref). An example usage to download the map of London to `"london.json"`:

```julia
OSM.download_osm_network(
    :place_name;
    place_name = "London",
    save_to_file_location = "london.json"
)
```

The length of an edge between two nodes is specified in the units of the map's `weight_type` as listed in the documentation for [`LightOSM.OSMGraph`](https://deloittedigitalapac.github.io/LightOSM.jl/docs/types/#LightOSM.OSMGraph). The possible `weight_type`s are:

  * `:distance`: The distance in kilometers of an edge
  * `:time`: The time in hours to travel along an edge at the maximum speed allowed on that road
  * `:lane_efficiency`: Time scaled by number of lanes

The default `weight_type` used is `:distance`.

All `kwargs` are propagated to [`LightOSM.graph_from_file`](https://deloittedigitalapac.github.io/LightOSM.jl/docs/create_graph/#LightOSM.graph_from_file).

## Routing with OSM

You can use [`plan_route!`](@ref) or [`plan_random_route!`](@ref). To actually move along a planned route use [`move_along_route!`](@ref).
