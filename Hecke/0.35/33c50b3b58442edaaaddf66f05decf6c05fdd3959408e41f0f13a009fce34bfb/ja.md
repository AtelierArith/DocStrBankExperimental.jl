```
ramification_group(K::AbsSimpleNumField, P::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, m::Map) -> Grp, GrpToGrp
```

数体 $K$ の素イデアル $P$ と `automorphism_group(K)` から返されるマップ `m` が与えられたとき、$P$ の分岐群を `m` の定義域の部分群として返します。
