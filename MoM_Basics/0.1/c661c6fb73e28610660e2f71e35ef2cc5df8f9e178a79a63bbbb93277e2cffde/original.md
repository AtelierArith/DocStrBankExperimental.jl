```
TriangleInfo{IT<: Integer, FT<:AbstractFloat} <: SurfaceCellType{IT, FT}
```

构成四面体的三角形信息结构体：

```
isbd        ::Bool                  是否在边界上
δκ          ::Complex{FT}           面两侧介质对比度差值
vertices    ::MMatrix{3, 3, FT, 9}  三角形3个角点坐标，每列为一个点
edgel       ::MVec3D{FT}            三边长
edgev̂       ::MMatrix{3, 3, FT, 9}  三个边的指向向量
edgen̂       ::MMatrix{3, 3, FT, 9}  三个边的外法向量
```

合理安排位置后，三个基函数的自由端即为三角形三个点的顺序。
