```julia
setobject!(
    vis::MeshCat.AbstractVisualizer,
    geom::MeshCat.GeometryLike
) -> MeshCat.Visualizer

```

This will construct an appropriate three.js object from the given geometry and a default material.
