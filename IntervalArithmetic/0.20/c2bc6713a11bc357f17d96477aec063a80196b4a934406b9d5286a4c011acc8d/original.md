```
mince(x::IntervalBox, ncuts::::NTuple{N,Int})
```

Splits `x[i]` in `ncuts[i]` intervals . These intervals are combined in all possible `IntervalBox`-es, which are returned as a vector.
