```
deflation(p::PolyRingElem)
```

Return a tuple `(shift, defl)` where `shift` is the exponent of the trailing term of $p$ and `defl` is the gcd of the distance between the exponents of the nonzero terms of $p$. If $p = 0$, both `shift` and `defl` will be zero.
