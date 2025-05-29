```
Translation(v) <: AbstractAffineMap
Translation(dx, dy)         # 2D
Translation(dx, dy, dz)     # 3D
```

Cartesian点をオフセット `v = (dx, dy, ...)` で移動させるための `Translation` 変換を構築します。
