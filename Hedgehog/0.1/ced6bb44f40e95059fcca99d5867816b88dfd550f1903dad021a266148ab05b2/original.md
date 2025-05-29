```
FlatRateCurve{R <: Number, S <: Number} <: AbstractRateCurve
```

Represents a flat curve with a constant continuously compounded zero rate.

# Fields

  * `reference_date::R`: The reference date for the curve, in internal tick units.
  * `rate::S`: The constant zero rate applied across all tenors.
