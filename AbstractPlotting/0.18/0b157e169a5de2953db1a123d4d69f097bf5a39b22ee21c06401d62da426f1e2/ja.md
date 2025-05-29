```
convert_arguments(Mesh, xyz::AbstractVector)::GLNormalMesh
```

入力メッシュとメッシュの頂点を表すベクトル `xyz` を受け取り、`xyz` の各三つ組が三角形を形成するという仮定の下でインデックスを作成します。
