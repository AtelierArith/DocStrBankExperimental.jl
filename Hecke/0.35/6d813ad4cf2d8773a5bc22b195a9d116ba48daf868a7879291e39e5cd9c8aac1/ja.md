```
formal_inverse(E::EllipticCurve, prec::Int) -> LaurentSeriesElem
```

形式的な冪級数 i を返します。これは、F(z, i(z)) = 0 の性質を持ち、ここで F は E の形式的群法則であり、パラメータ z = -x/y に関して O(z^prec) までのものです。
