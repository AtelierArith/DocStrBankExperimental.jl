```
DataDomain(domain::JutulDomain; property1 = p1, property2 = p2, ...)
```

エンティティに関連付けられたデータを保存するためのドメインのラッパーです。

例:

```julia
# 6つのセルと7つの内部面を持つグリッド
g = CartesianMesh((2, 3))
d = DataDomain(g)
d[:cell_vec] = rand(6) #ok, 同じく:
d[:cell_vec, Cells()] = rand(6) #ok
d[:cell_vec, Faces()] = rand(6) #not ok!
d[:face_vec, Faces()] = rand(7) #ok!
# 最後の次元がエンティティ次元と等しい場合、一般的な配列も追加できます
d[:cell_vec, Cells()] = rand(10, 3, 6) #ok
# 一般的なデータも追加できますが、指定する必要があります
d[:not_on_face_or_cell, nothing] = rand(3) # これもok
```
