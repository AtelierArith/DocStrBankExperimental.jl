```
lift(R::FqPolyRing, a::FqFieldElem) -> FqPolyRingElem
```

基底体の多項式環を `a` の親の基底体上に与えられたとき、`parent(a)(lift(R, a)) == a` が `true` となるようなリフトを返します。
