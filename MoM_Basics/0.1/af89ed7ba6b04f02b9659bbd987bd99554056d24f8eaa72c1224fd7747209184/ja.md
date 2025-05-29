```
HexahedraInfo{IT<: Integer, FT<:AbstractFloat, CT<:Complex} <: VolumeCellType{IT, FT, CT}
```

六面体情報構造体：

```
hexaID      ::IT                    番号
volume      ::FT                    体積
ε           ::CT                    相対誘電率
κ           ::CT                    媒体コントラスト
center      ::MVec3D{FT}            中心座標
verticesID  ::MVector{8, IT}        所在ノードID
vertices    ::MMatrix{3, 8, FT,24}  六面体4つの角点座標、各列が1つの点
facesn̂      ::MMatrix{3, 8, FT,24}  4つの面の外法線ベクトル
facesvid    ::MMatrix{3, 8, IT,24}  4つの面に含まれる4つのID
facesArea   ::MVector{6, FT}        4つの面の面積（unitriの正負部分に基づいて符号を付与）
faces       ::Vector{Quads4Hexa{IT, FT}}    4つの面の具体的情報
inBfsID     ::Vector{IT}            六面体が存在する基底関数のID
```
