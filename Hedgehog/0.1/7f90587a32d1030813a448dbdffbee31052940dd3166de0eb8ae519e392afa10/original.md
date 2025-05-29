```
RateCurve(reference_date::Real, tenors::AbstractVector, dfs::AbstractVector; interp = ...)
```

Constructs a `RateCurve` from discount factors and tenors.

# Arguments

  * `reference_date`: Time reference in internal tick units.
  * `tenors`: Vector of year fractions (must be sorted and non-empty).
  * `dfs`: Discount factors matching each tenor.
  * `interp`: A builder function `(u, t) -> interpolator` mapping zero rates and tenors to an interpolation object.

# Returns

  * A `RateCurve` instance.
