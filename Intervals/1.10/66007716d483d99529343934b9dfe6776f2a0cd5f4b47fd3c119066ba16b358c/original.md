```
maximum(interval::AbstractInterval{T}; [increment]) -> T
```

The maximum value contained within the `interval`.

If right-closed, returns `last(interval)`. If right-open, returns `first(interval) + eps(first(interval))` If right-unbounded, returns maximum value possible for type `T`.

A `BoundsError` is thrown for empty intervals or when the increment results in a maximum value not-contained by the interval.
