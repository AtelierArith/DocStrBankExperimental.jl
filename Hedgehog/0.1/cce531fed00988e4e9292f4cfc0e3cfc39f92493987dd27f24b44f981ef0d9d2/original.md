```
RateCurve(reference_date::Date, tenors::AbstractVector, dfs::AbstractVector; interp = ...)
```

Date-based overload for `RateCurve`.

# Arguments

  * `reference_date`: A `Date` object.
  * `tenors`: Vector of year fractions.
  * `dfs`: Discount factors.
  * `interp`: Interpolator builder.

# Returns

  * A `RateCurve` instance.
