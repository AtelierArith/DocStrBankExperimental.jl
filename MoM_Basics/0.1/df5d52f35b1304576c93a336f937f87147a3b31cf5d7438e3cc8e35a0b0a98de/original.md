```
TetrahedraInfo{IT<: Integer, FT<:AbstractFloat, CT<:Complex} <: VolumeCellType{IT, FT, CT}
```

四面体信息结构体：

```
tetraID     ::IT                    编号
volume      ::FT                    体积
ε           ::CT                    相对介电常数
κ           ::CT                    介质对比度
center      ::MVec3D{FT}            中心坐标
verticesID  ::MVector{4, IT}        所在节点id
vertices    ::MMatrix{3, 4, FT, 12} 四面体4个角点坐标，每列为一个点
facesn̂      ::MMatrix{3, 4, FT, 12} 四个面的外法向量
facesvid    ::MMatrix{3, 4, IT, 12} 四个面包含的三个id
facesArea   ::MVector{4, FT}        四个面的面积（根据为unitri正负部分赋予正负号）
faces       ::Vector{Tris4Tetra{IT, FT}}    四个面的具体信息
inBfsID     ::Vector{IT}            四面体所在的基函数的ID
```
