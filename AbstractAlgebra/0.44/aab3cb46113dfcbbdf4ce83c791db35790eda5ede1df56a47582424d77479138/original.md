```
gcd_with_cofactors(a::T, b::T) where T <: RingElem
```

Return a tuple `(g, abar, bbar)` consisting of `g = gcd(a, b)` and cofactors `abar` and `bbar` with `a = g*abar` and `b = g*bbar`.
