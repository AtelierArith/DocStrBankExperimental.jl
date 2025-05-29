```
TriangleInfo{IT<: Integer, FT<:AbstractFloat} <: SurfaceCellType{IT, FT}
```

構成四面体の三角形情報構造体：

```
isbd        ::Bool                  境界上にあるかどうか
δκ          ::Complex{FT}           面の両側の媒質の対比度差
vertices    ::MMatrix{3, 3, FT, 9}  三角形の3つの角点の座標、各列が1つの点
edgel       ::MVec3D{FT}            3つの辺の長さ
edgev̂       ::MMatrix{3, 3, FT, 9}  3つの辺の指向ベクトル
edgen̂       ::MMatrix{3, 3, FT, 9}  3つの辺の外法線ベクトル
```

適切に位置を配置した後、3つの基底関数の自由端は三角形の3つの点の順序となります。
