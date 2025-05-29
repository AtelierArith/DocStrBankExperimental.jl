```
mince(x::IntervalBox, n::Int)
```

Splits `x` in `n` intervals in each dimension of the same diameter. These intervals are combined in all possible `IntervalBox`-es, which are returned as a vector.
