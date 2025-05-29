```
Quads4Hexa{IT<: Integer, FT<:AbstractFloat} <: SurfaceCellType{IT, FT}
```

单个构成六面体的四边形信息：

```
isbd        ::Bool                  是否在体区域边界，
δκ          ::Complex{FT}           介质对比度变化量，
vertices    ::MMatrix{3, 4, FT, 12} 四边形 4 个角点坐标，每列为一个点，
edgel       ::MVector{4, FT}        四个边长，
edgev̂       ::MMatrix{3, 4, FT, 12} 四个边的单位指向向量，
edgen̂       ::MMatrix{3, 4, FT, 12} 四个边的单位外法向量。
```

合理安排位置后，四个基函数的自由端即为四边形四个点的顺序。
