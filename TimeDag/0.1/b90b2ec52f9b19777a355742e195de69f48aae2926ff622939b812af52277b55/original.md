```
lag(x::Node, w::TimePeriod)
```

Construct a node which takes values from `x`, but lags them by period `w`.

!!! note
    For any constant, lagging by an amount of time is a no-op. This is because the constant is represented as a single value at the start of time (which will later appear at the start of the evaluation window).

