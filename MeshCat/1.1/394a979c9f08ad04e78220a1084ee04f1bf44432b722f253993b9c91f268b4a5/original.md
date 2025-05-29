```julia
setobject!(
    vis::MeshCat.AbstractVisualizer,
    geom::MeshCat.GeometryLike,
    material::MeshCat.AbstractMaterial
) -> MeshCat.Visualizer

```

This will construct an appropriate three.js object from the given geometry and the given material.
