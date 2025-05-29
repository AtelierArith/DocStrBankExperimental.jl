```
struct SemanticMeta <: DeviceLayout.Meta
    layer::Symbol
    index::Int = 1
    level::Int = 1
end
SemanticMeta(layer::String; kwargs...)
SemanticMeta(meta::Meta; kwargs...)
```

DeviceLayout-native representation of an object's layer information and attributes.

Semantic metadata refers to the meaning of an element without reference to a fixed encoding. For example, “this polygon is in the negative of the ground plane” is semantic, while “this polygon is in GDS layer 1, datatype 2” is not. The semantic metadata is used in the final `render` step, where a layout is converted from a `CoordinateSystem` to a representation corresponding to a particular output format (e.g., a `Cell` for GDSII). A call to `render!(cell::Cell{S}, cs::CoordinateSystem; map_meta = identity, kwargs...)` will use the `map_meta` function to map each `GeometryEntity`'s metadata to `GDSMeta`.

The `level` and `index` fields do not have a strict interpretation imposed by DeviceLayout. (In this sense they are similar to GDS `datatype`.) The suggested use is as follows:

  * `index` distinguishes numbered instances within a layer, for example in greyscale lithography or port numbering
  * `level` distinguishes instances of a layer occurring in different contexts, such as in a 3D stack where equivalent layers may be present in multiple levels
