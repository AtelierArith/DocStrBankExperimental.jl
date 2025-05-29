```
inflate(f::PolyRingElem, shift::Int64, n::Int64) -> PolyRingElem
```

Given a polynomial $f$ in $x$, return $f(x^n)*x^j$, i.e. multiply all exponents by $n$ and shift $f$ left by $j$.
