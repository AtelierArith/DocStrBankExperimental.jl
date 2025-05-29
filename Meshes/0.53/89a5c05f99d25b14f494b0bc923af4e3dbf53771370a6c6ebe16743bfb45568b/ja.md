```
faces(mesh, rank)
```

`mesh`の`rank`-面を持つイテレータを返します。

## 例

3D空間に埋め込まれた四面体のメッシュを考えます。すべての3面（すなわち要素）またはすべての2面（すなわち隣接する要素間のインターフェースである三角形）をループすることができます：

```julia
tetrahedrons = faces(mesh, 3)
triangles    = faces(mesh, 2)
segments     = faces(mesh, 1)
```
