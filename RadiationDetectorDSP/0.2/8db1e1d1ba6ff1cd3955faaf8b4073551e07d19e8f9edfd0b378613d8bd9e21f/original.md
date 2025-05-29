```
struct TrapezoidalChargeFilter <: AbstractRadNonlinearFilter
```

Filter that responds to a step signal with a trapezoidal pulse.

The filter is equivalent to two moving averages separated by a gap.

Constructors:

  * `TrapezoidalChargeFilter(; fields...)`

Fields:

  * `avgtime::Union{Real, Unitful.AbstractQuantity{<:Real}}`: pre-rise averaging time
  * `gaptime::Union{Real, Unitful.AbstractQuantity{<:Real}}`: gap time
  * `avgtime2::Union{Real, Unitful.AbstractQuantity{<:Real}}`: post-rise averaging time

A sharp step on the input will result in a trapezoid with rise time and fall time `avgtime` and a flat top of length `gaptime`.
