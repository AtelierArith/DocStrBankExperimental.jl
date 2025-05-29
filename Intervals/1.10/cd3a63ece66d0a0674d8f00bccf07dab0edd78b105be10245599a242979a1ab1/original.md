```
minimum(interval::AbstractInterval{T}; [increment]) -> T
```

The minimum value contained within the `interval`.

If left-closed, returns `first(interval)`. If left-open, returns `first(interval) + eps(first(interval))` If left-unbounded, returns minimum value possible for type `T`.

A `BoundsError` is thrown for empty intervals or when the increment results in a minimum value not-contained by the interval.
