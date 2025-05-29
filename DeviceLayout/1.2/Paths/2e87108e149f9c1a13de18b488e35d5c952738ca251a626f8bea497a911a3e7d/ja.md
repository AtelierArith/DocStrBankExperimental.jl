```
function route!(path::Path{S}, p_end::Point, α_end, rule::RouteRule, sty=Paths.contstyle1(path);
                waypoints=Point{S}[], waydirs=Vector{typeof(1.0°)}(undef, length(waypoints)))) where {S}
```

`path`を`p_end`に到達角度`α_end`で拡張し、`RouteRule`に従います。デフォルトの実装は

```
reconcile!(path, p_end, α_end, rule, waypoints, waydirs)
_route!(path, p_end, α_end, rule, sty, waypoints, waydirs)
```

その後、エンドポイントが正常に到達したことを確認します。
