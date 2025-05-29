Variation of `setprop!` which accepts an explicit type for the underlying JS property. This property type is only used within an animation context.

```julia
setprop!(
    vis::MeshCat.Visualizer,
    property::AbstractString,
    jstype::AbstractString,
    value
) -> MeshCat.Visualizer

```
