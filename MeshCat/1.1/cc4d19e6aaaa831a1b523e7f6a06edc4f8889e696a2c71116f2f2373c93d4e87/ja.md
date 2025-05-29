```julia
setobject!(
    vis::MeshCat.AbstractVisualizer,
    geom::MeshCat.GeometryLike
) -> MeshCat.Visualizer

```

これは、指定されたジオメトリとデフォルトのマテリアルから適切な three.js オブジェクトを構築します。
