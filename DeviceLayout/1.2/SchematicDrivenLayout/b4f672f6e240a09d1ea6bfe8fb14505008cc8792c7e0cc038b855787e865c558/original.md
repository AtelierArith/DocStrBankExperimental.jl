```
halo(c::AbstractComponent, delta, inner_delta=nothing; only_layers=[], ignore_layers=[])
```

A component's halo, intended for use as an exclusion zone parameterized by a bias `delta`.

By default, this applies a `delta` halo to all `geometry` elements whose metadata matches the inclusion/exclusion requirements. For example, polygons are offset by `delta` (enlarged by growing `delta` away from each original edge). Any entities in layers in `ignore_layers` will be skipped. If `only_layers` is not empty, only those layers will be used to generate the halo. Layers for inclusion and exclusion can be provided as layer name `Symbol`s, in which case only the layer name needs to be matched, or as full `DeviceLayout.Meta` objects, in which case all metadata fields (e.g., index and level for `SemanticMeta`) must match.

An `inner_delta` may be specified to subtract the halo at that bias from the result.

`AbstractComponent`s may define their own `halo` methods.
