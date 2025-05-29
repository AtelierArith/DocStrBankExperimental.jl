```
halo(cs::CoordinateSystem, outer_delta, inner_delta=nothing; only_layers=[],
    ignore_layers=[])
halo(cs::Cell, outer_delta, inner_delta=nothing; only_layers=[], ignore_layers=[])
```

A coordinate system of type `typeof(cs)` with halos for all entities in `cs`, tracing through `cs.refs`.

Any entities in layers in `ignore_layers` will be skipped. If `only_layers` is not empty, only those layers will be used to generate the halo. Layers for inclusion and exclusion can be provided as layer name `Symbol`s, in which case only the layer name needs to be matched, or as full `DeviceLayout.Meta` objects, in which case all metadata fields (e.g., index and level for `SemanticMeta`) must match.

The orientations of polygons must be consistent, such that outer polygons share the same orientation, and any holes have the opposite orientation. Additionally, any holes should be contained within outer polygons; offsetting hole edges may create positive artifacts at corners.
