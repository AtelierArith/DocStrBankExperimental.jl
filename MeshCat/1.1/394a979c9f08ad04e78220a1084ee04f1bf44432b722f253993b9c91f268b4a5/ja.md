```julia
setobject!(
    vis::MeshCat.AbstractVisualizer,
    geom::MeshCat.GeometryLike,
    material::MeshCat.AbstractMaterial
) -> MeshCat.Visualizer

```

これは、与えられたジオメトリと与えられたマテリアルから適切な three.js オブジェクトを構築します。
