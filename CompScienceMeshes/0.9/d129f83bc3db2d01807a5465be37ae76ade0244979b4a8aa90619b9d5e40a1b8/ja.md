```
meshsphere(radius::F, h::F) where F
```

は Mesh(vertices, faces) を返します。

この関数は、半径とエッジ長を持つ球の単純な面積メッシュを生成します。さらに、この関数は kwargs - generator, delaunay - を受け取ります。 - generator :compsciencemeshes - がデフォルトです。 - delaunay –- は compsciencemeshes のための唯一の kwarg 引数です。 :(2D) - がデフォルトで、三角形分割は 2D デローニであり、中程度から大きなメッシュに対しては 3D の対応物よりもかなり速いです。三角形分割は x および y の頂点に対して行われ、頂点の z 座標は Stereographic 投影を使用して x, y から計算されます。 :(3D) - は三角形分割のために 3D デローニを呼び出し、中程度から大きなメッシュに対してはかなり遅くなります。 :gmsh - は gmsh を使用してメッシュを返します。

delaunay kwarg は compsciencemeshes のための唯一の引数です。generator kwarg は delaunay よりも優先されます。

関数 - gmshsphere も参照してください。
