```
FlatRateCurve(rate::Number; reference_date::TimeType = Date(0))
```

Creates a flat curve with constant zero rate.

# Arguments

  * `rate`: The constant continuously compounded rate.
  * `reference_date`: The reference date (default is the Julia epoch).

# Returns

  * A `FlatRateCurve` instance.
