```
formal_inverse(E::EllipticCurve, prec::Int) -> LaurentSeriesElem
```

Return the formal power series i with the property that F(z, i(z)) = 0 where F is the formal group law of E in terms of the parameter z= -x/y up to O(z^prec).
