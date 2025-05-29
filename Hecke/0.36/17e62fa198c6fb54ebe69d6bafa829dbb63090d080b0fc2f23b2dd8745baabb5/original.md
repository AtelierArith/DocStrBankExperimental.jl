```
anti_uniformizer(P::NumFieldOrderIdeal) -> NumFieldElem
```

Given a prime ideal $P$, returns an element $a$ in the number field containing $P$ with valuation(a, P) == -1, valuation(a, Q) = 0 at the prime conjugate to $P$ and non-negative valuation at all other prime ideals.
