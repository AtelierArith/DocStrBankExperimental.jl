```
convert_arguments(Mesh, x, y, z, indices)::GLNormalMesh
```

実数ベクトル x, y, z を取り、それらを使用して三角形メッシュを構築します。`indices` には整数（3つごとに1つの三角形）または GeometryBasics.NgonFace{N, <: Integer} を使用できます。
