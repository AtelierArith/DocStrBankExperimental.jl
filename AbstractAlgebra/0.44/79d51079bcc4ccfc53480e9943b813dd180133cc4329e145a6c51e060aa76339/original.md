```
compose(f::AbsPowerSeriesRingElem, g::AbsPowerSeriesRingElem; inner)
```

Compose the series $a$ with the series $b$ and return the result.

  * If `inner = :second`, then `f(g)` is returned and `g` must have positive valuation.
  * If `inner = :first`, then `g(f)` is returned and `f` must have positive valuation.
