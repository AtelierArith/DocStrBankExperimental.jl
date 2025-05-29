```
yearfrac(start, stop)
```

Compute the ACT/365 year fraction between two time points.

Inputs `start` and `stop` can be `Date`, `DateTime`, or ticks (`Int` or `Float64`). If ticks are provided, they are assumed to be milliseconds since the Julia `Dates` module epoch (0000-01-01T00:00:00), consistent with the output of `to_ticks`.
