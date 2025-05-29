```
orthogonal_projection(V::AbstractSpace, M::T) where T <: MatElem -> AbstractSpaceMor
```

空間 `V` と基底行列 `M` を持つ非退化部分空間 `W` が与えられたとき、`V` における `W` の補空間への射影に対応する `V` の自己準同型を返します。
