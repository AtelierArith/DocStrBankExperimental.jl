```
Quads4Hexa{IT<: Integer, FT<:AbstractFloat} <: SurfaceCellType{IT, FT}
```

単一の六面体を構成する四辺形情報：

```
isbd        ::Bool                  体領域の境界にあるかどうか，
δκ          ::Complex{FT}           媒質のコントラスト変化量，
vertices    ::MMatrix{3, 4, FT, 12} 四辺形の4つの角点座標，各列が1つの点，
edgel       ::MVector{4, FT}        4つの辺の長さ，
edgev̂       ::MMatrix{3, 4, FT, 12} 4つの辺の単位指向ベクトル，
edgen̂       ::MMatrix{3, 4, FT, 12} 4つの辺の単位外法線ベクトル。
```

適切に配置した後、4つの基底関数の自由端は四辺形の4つの点の順序となる。
