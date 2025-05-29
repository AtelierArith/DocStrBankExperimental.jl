```
lift(R::FqPolyRing, a::FqFieldElem) -> FqPolyRingElem
```

基底体の多項式環を与えられた `a` の親の上に、`parent(a)(lift(R, a)) == a` が `true` となるようなリフトを返します。
