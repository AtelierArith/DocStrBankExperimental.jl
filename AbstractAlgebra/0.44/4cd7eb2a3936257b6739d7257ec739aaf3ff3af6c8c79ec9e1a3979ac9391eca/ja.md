```
deflate(f::PolyRingElem, shift::Int64, n::Int64) -> PolyRingElem
```

多項式 $g$ が $x^n$ の形であり、`f = g(x)*x^{shift}` であるとき、$f$ を $x$ の多項式として書き換えます。すなわち、$g$ のすべての指数を $n$ で割ります。
