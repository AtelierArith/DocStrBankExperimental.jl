```
RateCurve(reference_date::Date, itp::I, builder::F) where {I, F}
```

Constructs a `RateCurve` from pre-built interpolation components and a `Date`.

# Arguments

  * `reference_date`: The date of the curve.
  * `itp`: A `DataInterpolations.AbstractInterpolation` object.
  * `builder`: The interpolator reconstruction function.

# Returns

  * A `RateCurve` instance.
