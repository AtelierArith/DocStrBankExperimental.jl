このビジュアライザーのパスの変換を設定します。これは、そのパスにオブジェクトを追加する前でも後でも行うことができます。

```julia
settransform!(
    vis::MeshCat.Visualizer,
    tform::CoordinateTransformations.Transformation
) -> MeshCat.Visualizer

```

オブジェクトの全体的な変換は、そのすべての親の変換の合成であるため、`vis[:group1]`の変換を設定すると、`vis[:group1][:box1]`および`vis[:group1][:box2]`のオブジェクトのポーズに影響を与えます。
