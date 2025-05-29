```
isatomic(x::Interval)
```

Check whether an interval `x` is *atomic*, i.e. is unable to be split. This occurs when the interval is empty, or when the upper bound equals the lower bound or the `nextfloat` of the lower bound.
