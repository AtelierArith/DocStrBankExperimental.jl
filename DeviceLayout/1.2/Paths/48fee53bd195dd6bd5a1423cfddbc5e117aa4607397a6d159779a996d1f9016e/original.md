```
reconcile!(path::Path, endpoint::Point, end_direction, rule::RouteRule, waypoints, waydirs;
    initialize_waydirs = false)
```

Ensure that `path` can be routed to `endpoint` at `end_direction` using `rule, waypoints, waydirs`, or throw an error.

Does nothing for a generic `RouteRule`. Subtypes of `RouteRule` may implement specialized methods to do their own validation when `route!` is called.

May insert inferred constraints to `waypoints` and `waydirs` to allow the path to be drawn leg-by-leg. For example, `reconcile!` with `rule::StraightAnd90`, no waypoints, and `α1(path) == end_direction` will insert a waypoint halfway between `p1(path)` and `endpoint`, allowing two successive `StraightAnd90` legs with opposite bends.
