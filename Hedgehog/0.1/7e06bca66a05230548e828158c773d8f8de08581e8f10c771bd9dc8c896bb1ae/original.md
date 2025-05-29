```
to_ticks(x::DateTime)
```

Convert a `DateTime` to milliseconds since the Julia `Dates` module epoch (0000-01-01T00:00:00).

Uses `Dates.datetime2epochms`.
