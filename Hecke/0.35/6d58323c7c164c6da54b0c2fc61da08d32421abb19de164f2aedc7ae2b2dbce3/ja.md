```
formal_w(E::EllipticCurve, prec::Int) -> LaurentSeriesElem
```

無限大での w = -1/y の形式展開を、パラメータ z = -x/y に関して O(z^prec) まで返します。
