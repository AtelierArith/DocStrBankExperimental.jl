```
deflate(x::PolyRingElem) -> PolyRingElem, Int
```

Deflate the polynomial $f$ maximally, i.e. find the largest $n$ s.th. $f$ can be deflated by $n$, i.e. $f$ is actually a polynomial in $x^n$. Return $g, n$ where $g$ is the deflation of $f$.
