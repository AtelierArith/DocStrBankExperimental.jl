```
struct Route{T<:RouteRule, S<:Coordinate}
Route(rule, startpoint::Point{S}, endpoint::Point, start_direction, end_direction; waypoints=Point{S}[], waydirs=[])
Route(rule, path0::Path, endpoint::Point, end_direction)
```

A `Route` implicitly defines a `Path` between two points with given start and end directions.

Use `Path(r::Route, sty::Paths.Style)` to create the explicit path.

Contains a `RouteRule` to determine how the `Path` should be drawn.

May contain `waypoints` and `waydirs` that additionally constrain the route. The `RouteRule` determines how these are handled, by default routing waypoint-to-waypoint such that the path starts at `p0`, passes through each point in `waypoints` in order, and then ends at `p1`.

If `waydirs` is not `nothing`, it should have the same length as `waypoints`. If `waydirs` is provided and is not ignored by the `RouteRule` (check the specific rule documentation), then `waypoints[i]` will be reached with the path pointing along `waydirs[i]`.
