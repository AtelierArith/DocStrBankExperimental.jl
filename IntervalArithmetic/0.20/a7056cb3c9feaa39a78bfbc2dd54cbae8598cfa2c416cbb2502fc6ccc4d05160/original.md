```
pow(x::Interval, n::Integer)
```

A faster implementation of `x^n`, currently using `power_by_squaring`. `pow(x, n)` will usually return an interval that is slightly larger than that calculated by `x^n`, but is guaranteed to be a correct enclosure when using multiplication with correct rounding.
