```
TimeSpan(start, stop)
```

Return `TimeSpan(Nanosecond(start), Nanosecond(stop))` representing the interval `[start, stop)`.

If `start == stop`, a single `Nanosecond` is added to `stop` since `stop` is an exclusive upper bound and TimeSpan operations only generally support up to nanosecond precision anyway.

The benefit of this type over e.g. `Nanosecond(start):Nanosecond(1):Nanosecond(stop)` is that instances of this type are guaranteed to obey `TimeSpans.start(x) < TimeSpans.stop(x)` by construction.
