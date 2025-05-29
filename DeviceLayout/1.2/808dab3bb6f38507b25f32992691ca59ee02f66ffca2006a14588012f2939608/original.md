```
to_polygons(ent::GeometryEntity; kwargs...)
```

Return a single polygon, an iterator, or `Vector` of `Polygon`s equivalent to `ent`.

If `ent` is a `StyledEntity`, all styles will be applied before conversion to polygons.
