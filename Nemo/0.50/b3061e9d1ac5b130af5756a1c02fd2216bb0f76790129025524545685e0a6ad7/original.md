```
rescale!(a::ZZLaurentSeriesRingElem)
```

Rescale the polynomial underlying the series so that the GCD of its exponents is 1. This is only used internally, since the result of every user facing function is a rescaled series.
