```
TriangleInfo{IT<: Integer, FT<:AbstractFloat} <: SurfaceCellType{IT, FT}
```

三角形情報構造体：

```
triID       ::IT                    番号
area        ::FT                    面積
verticesID  ::MVector{3, IT}        所在ノードID
vertices    ::MMatrix{3, 3, FT, 9}  三角形の3つの角点座標、各列が1つの点
center      ::MVec3D{FT}            中心座標
facen̂       ::MVec3D{FT}            面の外法線ベクトル
edgel       ::MVec3D                3辺の長さ
edgev̂       ::MMatrix{3, 3, FT, 9}  3つの辺の指向ベクトル
edgen̂       ::MMatrix{3, 3, FT, 9}  3つの辺の外法線ベクトル
inBfsID     ::MVector{3, IT}        三角形が所在する3つの基関数のID
```

合理的に配置した後、3つの基関数の自由端は三角形の3つの点の順序となる。
