```
roots(Q::QadicField, f::ZZPolyRingElem; max_roots::Int = degree(f)) -> Vector{QadicFieldElem}
```

The roots of $f$ in $Q$, $f$ has to be square-free (at least the roots have to be simple roots).
