```
MeshElement(nodenum, material, theta)
```

メッシュ内の要素で、4つの順序付けられたノード、材料、および繊維の方向から構成されています。

# 引数

  * `nodenum::Vector{integer}`: ノードインデックス。左下のノードから反時計回りに定義されています（局所座標系で定義されているように、図を参照してください）。
  * `material::Material`: 材料特性
  * `theta::float`: 繊維の方向
