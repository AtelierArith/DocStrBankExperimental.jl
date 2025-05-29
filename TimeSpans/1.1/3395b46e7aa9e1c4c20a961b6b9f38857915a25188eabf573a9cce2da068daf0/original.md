```
istimespan(x)
```

Return `true` if `x` has been declared to support `TimeSpans.start(x)` and `TimeSpans.stop(x)`, return `false` otherwise.

Types that overload `TimeSpans.start`/`TimeSpans.stop` should also overload `istimespan`.
