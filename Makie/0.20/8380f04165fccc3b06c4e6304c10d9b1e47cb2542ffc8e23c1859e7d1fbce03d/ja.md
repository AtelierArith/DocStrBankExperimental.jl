```
convert_arguments(Mesh, x, y, z, indices)::GLNormalMesh
```

実数ベクトル x, y, z を取り、それらを使用して三角形メッシュを構築します。`indices` に含まれる面は整数（3つごとに1つの三角形）または GeometryBasics.NgonFace{N, <: Integer} であることができます。
