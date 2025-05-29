```
RWG{IT<:Integer , FT<:AbstractFloat} <: LinearBasisFunction
```

RWG基関数複合型：

```
isbd        ::Bool              境界元であるかどうか、ブール型
bfID        ::IT                基関数番号、整数型
edgel       ::FT                基関数辺の長さ、浮動小数点型
inGeo       ::MVector{2, IT}    基関数が存在する2つの三角形の番号（半基関数は1つ、同じ2つに設定）、長さ2のベクトル配列
inGeoID     ::MVector{2, IT}    基関数が上記2つの三角形内での局所番号（半基関数は1つ、同じ2つに設定）、値は1:3、長さ2のベクトル配列
center      ::MVec3D{FT}        基関数の中心、オクツリーのグループ化に使用
```
