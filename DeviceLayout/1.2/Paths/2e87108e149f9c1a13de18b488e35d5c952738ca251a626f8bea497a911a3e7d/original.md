```
function route!(path::Path{S}, p_end::Point, α_end, rule::RouteRule, sty=Paths.contstyle1(path);
                waypoints=Point{S}[], waydirs=Vector{typeof(1.0°)}(undef, length(waypoints)))) where {S}
```

Extend `path` to `p_end` with arrival angle `α_end` according to `RouteRule`. The default implementation is

```
reconcile!(path, p_end, α_end, rule, waypoints, waydirs)
_route!(path, p_end, α_end, rule, sty, waypoints, waydirs)
```

followed by checking that the endpoint was successfully reached.
