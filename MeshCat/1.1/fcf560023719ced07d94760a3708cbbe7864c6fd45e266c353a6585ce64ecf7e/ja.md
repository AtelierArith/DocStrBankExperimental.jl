このビジュアライザーのパスにオブジェクトを設定します。これは、そのパスに現在存在するジオメトリを置き換えます。

```julia
setobject!(
    vis::MeshCat.Visualizer,
    obj::MeshCat.AbstractObject
) -> MeshCat.Visualizer

```

複数のジオメトリを描画するには、スライス表記を使用して異なるパスに配置します：

```
setobject!(vis[:group1][:box1], geometry1)
setobject!(vis[:group1][:box2], geometry2)
```
