```
RateCurve{F, R <: Real, I <: DataInterpolations.AbstractInterpolation} <: AbstractRateCurve
```

Represents an interpolated rate curve based on zero rates derived from input discount factors.

# Fields

  * `reference_date::R`: The reference date for the curve, represented in internal tick units (e.g., milliseconds since epoch).
  * `interpolator::I`: An interpolation object (from `DataInterpolations.jl`) representing the zero rate curve as a function of year fractions.
  * `builder::F`: A function `(u, t) -> interpolator` used to reconstruct the interpolator (e.g., during calibration), where `u` are zero rates and `t` are year fractions.
