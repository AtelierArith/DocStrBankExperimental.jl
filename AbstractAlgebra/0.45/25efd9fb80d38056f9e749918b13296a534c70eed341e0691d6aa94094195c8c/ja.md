```
inflate(f::PolyRingElem, shift::Int64, n::Int64) -> PolyRingElem
```

多項式 $f$ を $x$ で与えられたとき、$f(x^n)*x^j$ を返します。すなわち、すべての指数を $n$ 倍し、$f$ を $j$ だけ左にシフトします。
