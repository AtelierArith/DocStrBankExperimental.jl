```
inside = isinside_closed_STL(mesh::Mesh, Pt, eps=1e-3)
```

点 `Pt` が3Dの閉じた三角形 `*.stl` サーフェスの内部にあるかどうかを判断します。

これは、以下のpythonコードに従って、ワインディングナンバー法を実装しています: https://github.com/marmakoide/inside-3d-mesh

これは、Alec Jacobson、Ladislav Kavan、Olga Sorkine-Hornungによる以下の[論文](https://igl.ethz.ch/projects/winding-number/)でも説明されています。
