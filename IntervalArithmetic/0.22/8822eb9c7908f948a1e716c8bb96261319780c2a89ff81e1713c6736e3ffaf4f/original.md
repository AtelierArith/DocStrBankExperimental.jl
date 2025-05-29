```
Domain{LeftBound, RightBound}(lo, hi)
```

The domain of a function.

`LeftBound` and `RightBound` must be symbols and are either `:closed` or `:open` determining if the corresponding endpoint is (respectively) included or not in the domain.

If `hi > lo`, the domain is considered to be empty.
