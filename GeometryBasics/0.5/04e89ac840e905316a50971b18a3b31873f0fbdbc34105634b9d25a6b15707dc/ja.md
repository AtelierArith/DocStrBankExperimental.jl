```
per_face(data, faces)
per_face(data, mesh)
```

与えられたデータを頂点ごとではなく面ごとに適用する `FaceView` を生成します。結果は次のようにして (新しい) メッシュを作成するために使用できます：

```
mesh(..., attribute_name = per_face(data, faces))
mesh(old_mesh, attribute_name = per_face(data, old_mesh))
```
