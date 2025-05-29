```
move_along_route!(agent, model::ABM{<:OpenStreetMapSpace}, distance::Real) → remaining
```

Move an agent by `distance` along its planned route. Units of distance are as specified by the underlying graph's `weight_type`. If the provided `distance` is greater than the distance to the end of the route, return the remaining distance. Otherwise, return `0`. `0` is also returned if `is_stationary(agent, model)`.
