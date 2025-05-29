指定されたパスのオブジェクトに対して単一のプロパティを設定します。

```julia
setprop!(
    vis::MeshCat.Visualizer,
    property::AbstractString,
    value
) -> MeshCat.Visualizer

```

（これは、Julia v0.7で導入されたBase.setproperty!関数との混乱を避けるためにsetprop!と名付けられています）
