```
compose(f::PolyRingElem, g::PolyRingElem; inner)
```

Compose the polynomial $a$ with the polynomial $b$ and return the result.

  * If `inner = :right`, then `f(g)` is returned.
  * If `inner = :left`, then `g(f)` is returned.
