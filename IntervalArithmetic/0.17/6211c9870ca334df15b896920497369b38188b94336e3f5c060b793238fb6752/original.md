```
round(a::Interval[, RoundingMode])
```

Returns the interval with rounded to an interger limits.

For compliance with the IEEE Std 1788-2015, "roundTiesToEven" corresponds to `round(a)` or `round(a, RoundNearest)`, and "roundTiesToAway" to `round(a, RoundNearestTiesAway)`.
