```
renest(R::Union{PolyRing, MPolyRing}, g::MPolyRingElem)
```

入れ子になっていない対応物から反復多項式環 `R` の要素を返します。返される値は `f == renest(R, denest(denest(R), f))` を満たします。
