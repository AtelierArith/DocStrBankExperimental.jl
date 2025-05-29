```
maprange(f, start; stop, length)
maprange(f; start, stop, length)
maprange(f, start, stop; length)
```

`length` values between `start` and `stop`, so that `f(x)` is incremented in uniform steps. Uses `mapview` in order not to materialize the array.

`maprange(identity, ...)` is equivalent to `range(...)`. Most common application - log-spaced ranges:

`maprange(log, 10, 1000, length=5) ≈ [10, 31.6227766, 100, 316.227766, 1000]`

Other transformations can also be useful:

`maprange(sqrt, 16, 1024, length=5) == [16, 121, 324, 625, 1024]`
