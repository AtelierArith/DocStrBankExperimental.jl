```
plan_route!(agent, dest, model::ABM{<:OpenStreetMapSpace};
            return_trip = false, kwargs...) → success
```

Plan a route from the current position of `agent` to the location specified in `dest`, which can be an intersection or a point on a road. Overwrite any existing route.

If `return_trip = true`, a route will be planned from start ⟶ finish ⟶ start. All other keywords are passed to [`LightOSM.shortest_path`](https://deloittedigitalapac.github.io/LightOSM.jl/docs/shortest_path/#LightOSM.shortest_path).

Return `true` if a path to `dest` exists, and hence the route planning was successful. Otherwise return `false`. When `dest` is an invalid position, i.e. if it contains node indices that are not in the graph, or if the distance along the road is not between zero and the length of the road, return `false` as well. 

Specifying `return_trip = true` also requires the existence of a return path for a route to be planned.
