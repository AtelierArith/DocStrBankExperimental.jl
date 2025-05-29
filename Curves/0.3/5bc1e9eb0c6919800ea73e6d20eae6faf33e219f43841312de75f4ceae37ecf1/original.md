```
Curve(x:: AbstractVector{Tenor}, y:: AbstractVector; offset:: Real = 0, kwargs...)
```

Construct Curve objects from an array of Tenor objects strings as x-axis.

With the `offset` keyword argument the points on the x-axis, defined by the given tenors, can be shifted. This could be e.g. used to take a spot lag of financial instruments into account. Note that the shift is always in calendar days, a spot lag given in business days must be converted to calendar days beforehand.
