```
formal_differential_form(E::EllipticCurve, prec::Int) -> LaurentSeriesElem
```

f(z)の形式展開を返します。ここで、f(z)dzは、パラメータz = -x/yに関して無限大での不変微分dx/(2y + a*1 x + a*3)の形式展開であり、O(z^prec)までです。
