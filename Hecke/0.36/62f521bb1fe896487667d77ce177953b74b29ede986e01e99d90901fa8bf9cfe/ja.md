```
orthogonal_complement(V::AbstractSpace, M::T) where T <: MatElem -> T
```

空間 `V` と基底行列 `M` を持つ部分空間 `W` が与えられたとき、`V` 内の `W` の直交補空間の基底行列を返します。
