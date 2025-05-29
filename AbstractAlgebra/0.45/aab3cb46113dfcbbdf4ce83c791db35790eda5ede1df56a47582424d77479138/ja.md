```
gcd_with_cofactors(a::T, b::T) where T <: RingElem
```

`g = gcd(a, b)` と `a = g*abar` および `b = g*bbar` の共因子 `abar` と `bbar` からなるタプル `(g, abar, bbar)` を返します。
