```
halo(pa::Path, outer_delta, inner_delta; only_layers=[], ignore_layers=[])
```

Return a `Path` forming the halo of `pa`, equivalent to offsetting the geometry by `outer_delta`, then subtracting the offset by `inner_delta` if it is not `nothing`.

Extends the start and/or end by `delta` (for each inner/outer offset) when `pa` has nonzero extent at the endpoints. Each segment's style is the halo style of the original segment.

For the segments of the `Path` and any attached references, any entities in layers in `ignore_layers` will be skipped. Note that even if the segments are ignored, attachments may not be. If `only_layers` is not empty, only those layers will be used to generate the halo. Layers for inclusion and exclusion can be provided as layer name `Symbol`s, in which case only the layer name needs to be matched, or as full `DeviceLayout.Meta` objects, in which case all metadata fields (e.g., index and level for `SemanticMeta`) must match.

Returns a Path.
