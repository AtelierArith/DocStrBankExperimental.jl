```
route!(g::SchematicGraph, rule::RouteRule,
    nodehook1::Pair{ComponentNode,Symbol}, nodehook2::Pair{ComponentNode,Symbol},
    sty, meta;
    waypoints=[], waydirs=[], global_waypoints=false,
    name=uniquename("r_$(component(nodehook1.first).name)_$(component(nodehook2.first).name)"),
    kwargs...)
route!(g::SchematicGraph, rule::RouteRule, node1::ComponentNode, nodehook2::Pair{ComponentNode,Symbol}, sty, meta; kwargs...)
route!(g::SchematicGraph, rule::RouteRule, nodehook1::Pair{ComponentNode,Symbol}, node2::ComponentNode, sty, meta; kwargs...)
route!(g::SchematicGraph, rule::RouteRule, node1::ComponentNode, node2::ComponentNode, sty, meta; kwargs...)
```

Creates a `RouteComponent` with given style `sty` and metadata `meta`, and fuses it between the specified nodes and hooks in `g`.

Returns the resulting `ComponentNode` in `g`.

Example usage: `route!(g, BSplineRouting(), zline_node=>:feedline, z_launcher_node=>:line, Paths.CPW(10μm, 6μm), GDSMeta(1, 2))`

If one or both hook symbols are not specified, then `matching_hook` or `matching_hooks` will be used to attempt to automatically find the correct hook or hooks.

The route will have start and endpoints at the origin until a method like `plan!` is called. `waypoints` and `waydirs` are in component-local coordinates (unless `global_waypoints` is `true`), and `rule` determines how they will be used.

Additional keyword arguments will become vertex properties for the `RouteComponent`'s node.

`name` should be unique.
