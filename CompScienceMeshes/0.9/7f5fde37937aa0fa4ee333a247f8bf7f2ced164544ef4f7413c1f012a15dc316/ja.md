```
tetmeshcuboid(length::F, breadth::F, width::F, edge length::F) where F
```

は Mesh(vertices, faces) を返します。

関数は直方体の単体体積メッシュを返します。キーワード引数 - generator :compsciencemeshes - がデフォルトで、直方体の構造化された四面体メッシュを生成します。直方体の寸法はエッジの長さの倍数で近似されます -

```
各単位立方体には24の四面体があります - 各面に4つ - 
直方体には n*m*p の単位立方体があり、ここで n, m, p はそれぞれ長さ、幅、奥行きに沿ったセグメントの数です。
```

:gmsh - gmshを使用して直方体の四面体メッシュを返します。

また、gmsh関数 - tetgmshcuboid も参照してください。
