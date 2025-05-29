```
formal_differential_form(E::EllipticCurve, prec::Int) -> LaurentSeriesElem
```

Return the formal expansion of f(z) where f(z)dz is the invariant differential dx/(2y + a*1 x + a*3) at infinity in terms of parameter z= -x/y up to O(z^prec).
