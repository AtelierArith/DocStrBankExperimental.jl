```
flat_elements(geom::Union{GeometryStructure,GeometryReference}, only_layers=[], ignore_layers=[])
flat_elements(geom_layer::Pair{<:Union{GeometryStructure,GeometryReference}})
```

Return a list of `GeometryEntity` elements in flatten(cs), optionally filtering metadata.

`only_layers` and `ignore_layers` can be layer name `Symbol`s, `DeviceLayout.Meta`, or collections of either. The metadata filtering function is produced using [`layer_inclusion(only_layers, ignore_layers)`](@ref). This means that the default empty `only_layers` is the same as listing all layers.

Using an argument pair `geom => layer` is equivalent to `flat_elements(geom, layer)`.
