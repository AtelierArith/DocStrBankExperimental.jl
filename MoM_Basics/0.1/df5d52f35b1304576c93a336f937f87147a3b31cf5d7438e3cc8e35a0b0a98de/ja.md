```
TetrahedraInfo{IT<: Integer, FT<:AbstractFloat, CT<:Complex} <: VolumeCellType{IT, FT, CT}
```

四面体情報構造体：

```
tetraID     ::IT                    番号
volume      ::FT                    体積
ε           ::CT                    相対誘電率
κ           ::CT                    媒体コントラスト
center      ::MVec3D{FT}            中心座標
verticesID  ::MVector{4, IT}        所在ノードID
vertices    ::MMatrix{3, 4, FT, 12} 四面体4つの角点座標、各列が1つの点
facesn̂      ::MMatrix{3, 4, FT, 12} 4つの面の外法線ベクトル
facesvid    ::MMatrix{3, 4, IT, 12} 4つの面に含まれる3つのID
facesArea   ::MVector{4, FT}        4つの面の面積（unitriの正負部分に基づいて符号を付与）
faces       ::Vector{Tris4Tetra{IT, FT}}    4つの面の具体的情報
inBfsID     ::Vector{IT}            四面体が所在する基底関数のID
```
