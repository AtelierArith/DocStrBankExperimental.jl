```
faces(topology, rank)
```

`topology`の`rank`-面を持つイテレータを返します。

## 例

3D空間に埋め込まれた四面体のメッシュを考えます。すべての3面（別名要素）またはすべての2面（すなわち隣接する要素間のインターフェースである三角形）をループ処理できます：

```julia
tetrahedrons = faces(topology, 3)
triangles    = faces(topology, 2)
segments     = faces(topology, 1)
```
