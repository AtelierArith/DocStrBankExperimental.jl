```
render(mesh::Mesh; normals::Bool = false, wireframe::Bool = false, kwargs...)
```

`Mesh`オブジェクトをレンダリングします。これにより新しいビジュアライゼーションが作成されます（詳細はドキュメントを参照してください）。`normals = true`はメッシュ内の各三角形の法線ベクトルの方向に矢印を描画し、`wireframe = true`は各三角形のエッジを黒い線で描画します。キーワード引数は`Makie.mesh()`に渡されます。各三角形の実際の色はシーンの照明に依存しますが、`shading = false`を渡すことでこれをオフにすることが可能です。これにより、`Scene`オブジェクトで指定された正確な色が使用されます。
