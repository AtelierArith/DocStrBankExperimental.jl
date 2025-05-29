```
formal_log(E::EllipticCurve, prec::Int) -> LaurentSeriesElem
```

Eの形式的対数を、パラメータz = -x/yに関して無限大での冪級数としてO(z^prec)まで返します。
