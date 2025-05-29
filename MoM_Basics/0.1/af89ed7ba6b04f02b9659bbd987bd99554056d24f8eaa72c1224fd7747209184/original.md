```
HexahedraInfo{IT<: Integer, FT<:AbstractFloat, CT<:Complex} <: VolumeCellType{IT, FT, CT}
```

六面体信息结构体：

```
hexaID      ::IT                    编号
volume      ::FT                    体积
ε           ::CT                    相对介电常数
κ           ::CT                    介质对比度
center      ::MVec3D{FT}            中心坐标
verticesID  ::MVector{8, IT}        所在节点id
vertices    ::MMatrix{3, 8, FT,24}  六面体4个角点坐标，每列为一个点
facesn̂      ::MMatrix{3, 8, FT,24}  四个面的外法向量
facesvid    ::MMatrix{3, 8, IT,24}  四个面包含的四个id
facesArea   ::MVector{6, FT}        四个面的面积（根据为unitri正负部分赋予正负号）
faces       ::Vector{Quads4Hexa{IT, FT}}    四个面的具体信息
inBfsID     ::Vector{IT}            六面体所在的基函数的ID
```
