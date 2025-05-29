```
deflate(f::PolyRingElem, shift::Int64, n::Int64) -> PolyRingElem
```

Given a polynomial $g$ in $x^n$ such that `f = g(x)*x^{shift}`, write $f$ as a polynomial in $x$, i.e. divide all exponents of $g$ by $n$.
