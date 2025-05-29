```
make_halo(delta, inner_delta=nothing; only_layers=[], ignore_layers=[])
```

Returns a function `(c)->halo(c, delta, inner_delta; only_layers, ignore_layers)` for generating `GeometryStructure` halos.

Any entities in layers in `ignore_layers` will be skipped. If `only_layers` is not empty, only those layers will be used to generate the halo. Layers for inclusion and exclusion can be provided as layer name `Symbol`s, in which case only the layer name needs to be matched, or as full `DeviceLayout.Meta` objects, in which case all metadata fields (e.g., index and level for `SemanticMeta`) must match.
