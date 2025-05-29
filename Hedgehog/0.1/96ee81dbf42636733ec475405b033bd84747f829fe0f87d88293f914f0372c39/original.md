```
to_ticks(x::Real)
```

Assume `x` is already a timestamp in milliseconds since the Julia `Dates` module epoch (0000-01-01T00:00:00) and return it unchanged.

Used to normalize mixed inputs (e.g., `Date`, `DateTime`, `Real`) to a common tick representation for calculations like `yearfrac` or `add_yearfrac`.
