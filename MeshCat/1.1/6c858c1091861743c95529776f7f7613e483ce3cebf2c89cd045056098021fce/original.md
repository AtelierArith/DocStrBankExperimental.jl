Set a single property for the object at the given path.

```julia
setprop!(
    vis::MeshCat.Visualizer,
    property::AbstractString,
    value
) -> MeshCat.Visualizer

```

(this is named setprop! instead of setproperty! to avoid confusion with the Base.setproperty! function introduced in Julia v0.7)
