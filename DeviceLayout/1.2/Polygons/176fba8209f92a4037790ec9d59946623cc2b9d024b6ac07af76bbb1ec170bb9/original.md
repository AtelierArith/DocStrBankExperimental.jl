```
difference2d(p1, p2)
```

Return the geometric union of `p1` minus the geometric union of `p2` as a `ClippedPolygon`.

Each of `p1` and `p2` may be a `GeometryEntity` or array of `GeometryEntity`. All entities are first converted to polygons using [`to_polygons`](@ref).

Each of `p1` and `p2` can also be a `GeometryStructure` or `GeometryReference`, in which case `elements(flatten(p))` will be converted to polygons.

Each can also be a pair `geom => layer`, where `geom` is a `GeometryStructure` or `GeometryReference`, while `layer` is a `DeviceLayout.Meta`, a layer name `Symbol`, and/or a collection of either, in which case only the elements in those layers will be used.
