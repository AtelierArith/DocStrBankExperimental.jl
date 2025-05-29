```
nearest_point_on_way(g::OSMGraph, point::GeoLocation, way_id::DEFAULT_OSM_ID_TYPE)
```

Finds the nearest position on a way to a given point. Matches to an `EdgePoint`.

# Arguments

  * `g::OSMGraph`: LightOSM graph.
  * `point::GeoLocation`: Point to find nearest position to.
  * `wid::Integer`: Way ID to search.

# Returns

  * `::Tuple`:

      * `::EdgePoint`: Nearest position along the way between two nodes.
      * `::Float64`: Distance from `point` to the nearest position on the way.
