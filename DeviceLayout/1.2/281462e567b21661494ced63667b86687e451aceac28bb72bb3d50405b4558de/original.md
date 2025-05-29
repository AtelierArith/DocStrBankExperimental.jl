```
offset(ent::GeometryEntity,
    delta;
    j::Clipper.JoinType=Clipper.JoinTypeMiter,
    e::Clipper.EndType=Clipper.EndTypeClosedPolygon)
offset(ents,
    delta;
    j::Clipper.JoinType=Clipper.JoinTypeMiter,
    e::Clipper.EndType=Clipper.EndTypeClosedPolygon)
```

Return a `Vector` containing the result of offsetting boundaries outwards by `delta`.

Entities will be resolved into `Polygon`s using [`to_polygons`](@ref) before offsetting using Clipper with options `j` and `e`.

Offsetting is specifically a polygon operation, as performed by Clipper. An alternative method [`halo`](@ref) may be defined that produces an equivalent non-polygon `GeometryEntity`.
