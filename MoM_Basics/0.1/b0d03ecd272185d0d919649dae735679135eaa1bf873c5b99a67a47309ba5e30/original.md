```
TriangleInfo{IT<: Integer, FT<:AbstractFloat} <: SurfaceCellType{IT, FT}
```

三角形信息结构体：

```
triID       ::IT                    编号
area        ::FT                    面积
verticesID  ::MVector{3, IT}        所在节点id
vertices    ::MMatrix{3, 3, FT, 9}  三角形3个角点坐标，每列为一个点
center      ::MVec3D{FT}            中心坐标
facen̂       ::MVec3D{FT}            面的外法向量
edgel       ::MVec3D                三边长
edgev̂       ::MMatrix{3, 3, FT, 9}  三个边的指向向量
edgen̂       ::MMatrix{3, 3, FT, 9}  三个边的外法向量
inBfsID     ::MVector{3, IT}        三角形所在的三个基函数的ID
```

合理安排位置后，三个基函数的自由端即为三角形三个点的顺序。
