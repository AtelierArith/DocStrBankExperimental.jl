```
RBF{IT<:Integer , FT<:AbstractFloat} <: LinearBasisFunction
```

屋根基底関数 (Rooftop basis function, RBF) 基底関数複合型：

```
isbd        ::Bool              境界元即半基底関数であるかどうか、ブール型
bfID        ::IT                基底関数番号、整数型
inGeo       ::MVector{2, IT}    基底関数が存在する2つの六面体番号（半基底関数は1つ、同じ値を2つに設定）、長さ2のベクトル配列
inGeoID     ::MVector{2, IT}    基底関数が2つの六面体内での局所番号（半基底関数は1つ、同じ値を2つに設定）、値は1:4、長さ2のベクトル配列
center      ::MVec3D{FT}        基底関数の中心、オクツリーグループ化に使用
```
